pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
        PATH = "/opt/apache-maven-3.9.11/bin:$PATH"
    }
    stages {
        stage("Build"){
            steps {
                sh 'mvn clean deploy'
            }
        }
    

    stage('SonarQube analysis') {
    environment  {
        scannerHome = tool 'devopsmeister-sonar-scanner'
    }
    steps {
    withSonarQubeEnv('devopsmeister-sonarqube-server') { 
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }
}

}

