pipeline {

  agent any
  
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          echo "***MUNIT test case****"
      }
    }

     stage('Deployment') {
    
      steps {
            bat 'mvn -U -V -e -B -DskipTests -Ptest deploy -DmuleDeploy'
      }
    }
    
  }

  
}