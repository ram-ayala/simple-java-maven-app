pipeline {
    agent any
	tools {
        maven 'M2'
    }
	options {
        skipStagesAfterUnstable()
    }
	stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests -X clean package' 
            }
        }
		stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
		stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
            }
        }
		stage('Cat Directories') { 
            steps {
                sh 'ls -lrt /jenkins_home/jenkins/workspace/Ram-Test2/target/test-classes ' 
				sh 'ls -lrt /jenkins_home/jenkins/workspace/Ram-Test2/target/ '
            }
        }
    }
}