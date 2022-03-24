pipeline {
    agent any
     parameters{
     booleanParam(name: 'npmbuild',  description: 'perform npm build')


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
              sh 'docker build .'
}

}


     }
    }

