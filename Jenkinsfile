
node(){
    parameters{
        choice(
            choices: 'create\nupdate\nrollback',
            description: '',
            name: 'ACTION')
    }
    stage ('checkout'){
        git branch: '$BRANCH_NAME', changelog: false, credentialsId: '9440d5c3-c608-4ef7-9686-1b9b9d650495', poll: false, url: 'https://github.com/krapa999/cloudformation.git' 
    }
    /*
    stage ('Configure AWS'){
        sh 'sudo yum install python-pip -y'
        sh 'sudo yum install awscli -y'
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'jvinayak', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) 
        {
        sh '''aws --version
            aws configure set default.region us-east-1
            aws configure set aws_access_key_id ${AWS_ACCESS_KEY_ID}
            export aws_access_key=${AWS_ACCESS_KEY_ID}
            aws configure set aws_secret_access_key ${AWS_SECRET_ACCESS_KEY}
            export aws_secret_key=${AWS_SECRET_ACCESS_KEY}
            '''
        }

    }*/
    stage ('Validate template')
    {
        sh 'aws cloudformation validate-template --template-body file://sample-cfn.yml'
    }
    
   /*sh "echo ${ACTION}"    
   stage ('Stack Action')
   {
       if ( {params.ACTION} == "create")
       { 
           sh  "echo '${ACTION}'"
       }
       if ( "{params.ACTION}" == "update")
       {
           sh  "echo '${ACTION}'"
    
       } 
       if ( {params.ACTION} == "rollback")
       {
           sh  "echo '${ACTION}'"
      
       }
    }
    */
    stage ('Create') {
            when {
                // Only say hello if a "greeting" is requested
                expression { params.ACTION == 'create' }
            }
            steps {
                echo "Hello, bitwiseman!"
            }
    }
    stage ('Stack') {
            when {
                // Only say hello if a "greeting" is requested
                expression { params.ACTION == 'update' }
            }
            steps {
                echo "Hello, Update"
            }
    }
    


    
}
