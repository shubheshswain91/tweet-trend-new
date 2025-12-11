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
                echo "------------- Building the Application -------------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo "------------- Build Completed ---------------------"
            }
        }

        stage('Unit Tests') {
    steps {
        echo "------------- Running Unit Tests -------------"
        sh 'mvn surefire-report:report'
        echo "------------- Unit Tests Completed -------------"
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
  stage("Quality Gate"){
    steps{
        script{
            timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
            def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
            if (qg.status != 'OK') {
            error "Pipeline aborted due to quality gate failure: ${qg.status}"
        } 
        
    }
}

}

