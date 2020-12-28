pipeline {
    agent any
    

    environment {
        JAVA_HOME = "${jdk}"
    }

    stages {
        stage('Prepare') {
            agent { label 'test' }
            steps {
                checkout scm
            }
        }

        stage('Test') {
            agent { label 'test' }
            steps {
                sh 'mvn install'
            }
        }

        stage('QA') {
            agent { label 'test' }
            steps {
                withSonarQubeEnv('sonar') {
                    script {
                        echo "test"
                    }
                }
            }
        }
    }
}
