pipeline {
    agent any
     parameters{
     booleanParam(name: 'npmbuild',  description: 'perform npm build')}
  imageTag(name: 'DOCKER_IMAGE', image: 'jenkins/jenkins')
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
              sh 'docker build .'
               }

                         }
    
stage('Test') {
      steps {
        echo "$DOCKER_IMAGE"
        echo "$DOCKER_IMAGE_TAG" 
        echo "$DOCKER_IMAGE_IMAGE" 
      }
    }

 }
}
