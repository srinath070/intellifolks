pipeline {
    agent any
    node ( test )
    tools {
        jdk 'jdk10'
        maven 'M3'
    }

    environment {
        JAVA_HOME = "${jdk}"
    }

    stages {
        stage('Prepare') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh 'mvn install'
            }
        }

        stage('QA') {
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
