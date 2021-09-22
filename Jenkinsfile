pipeline {

  agent any
  environment{
	ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIALS')
  }
  
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
	
	environment{
		CLIENT_ID = credentials('TEST_CLIENT_ID')
		CLIENT_SECRET = credentials('TEST_CLIENT_SECRET')
	}
      steps {
            bat 'mvn -U -V -e -B -DskipTests -Ptest deploy -DmuleDeploy -Danypoint.username="%ANYPOINT_CREDS_USR%" -Danypoint.password="%ANYPOINT_CREDS_PSW%" -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret="%CLIENT_SECRET%"'
      }
    }
    
  }

  
}