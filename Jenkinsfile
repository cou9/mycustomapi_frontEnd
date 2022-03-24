pipeline {
    agent any
     parameters{
     booleanParam(name: 'npmbuild',  description: 'perform npm build')
       
      
   }
  stages {
     stage('npm build'){
           when{ expression { params.npmbuild == true } }   
           steps{
              sh "${params.npmbuild}"
              sh 'npm install'
              sh 'npm build'
 }
      }
     stage('docker build'){
          steps{
              sh 'docker biuld -f Dockerfile'
}

}


     }
    }
