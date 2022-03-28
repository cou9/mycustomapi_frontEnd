pipeline {
    agent any
     parameters{
     booleanParam(name: 'npmbuild',  description: 'perform npm build')
     string(name: 'DOCKER_IMAGE', description: 'jenkins/jenkins')
     }
       environment {
    AWS_DEFAULT_REGION="ap-south-1"
}
     
  stages {
     stage('npm build'){
           when{ expression { params.npmbuild == true } }
           steps{
               nodejs(nodeJSInstallationName: 'Node14') {
                    sh 'npm install'
                    sh 'npm run build'
                }

 }
}
     stage('docker build'){
          steps{
              script{
             sh 'docker build -t reactapp/myapi-app-1.0 .'
              }
         }
     }
     
   stage('docker push'){
            
            steps{
                withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials-cred', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                 script{
                     sh 'aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 557454388896.dkr.ecr.ap-south-1.amazonaws.com'
                     sh 'docker tag reactapp/myapi-app-1.0:latest 557454388896.dkr.ecr.ap-south-1.amazonaws.com/first_ecr_terra:latest'
                     sh 'docker push 557454388896.dkr.ecr.ap-south-1.amazonaws.com/first_ecr_terra:latest'
                 }
                 
                }
              }
   }
              

              
              
              
}

}
