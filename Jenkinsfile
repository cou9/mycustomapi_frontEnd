
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
              
}

}
    