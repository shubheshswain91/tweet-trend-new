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
                sh 'mvn -Dsurefire.argLine="-Xmx1024m -Xms512m" clean deploy'
            }
        }
    }
}
