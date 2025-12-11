pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
        PATH = "/opt/apache-maven-3.9.11/bin:$PATH"
        MAVEN_OPTS = "-Xmx512m -Xms256m"
    }
    stages {
        stage("Build"){
            steps {
                sh 'mvn clean deploy'
            }
        }
    }
}
