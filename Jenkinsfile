pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('Clone-repository') {
            steps {
                git branch: 'main', url: 'https://github.com/shubheshswain91/tweet-trend-new.git'
            }
        }
    }
}
