pipeline {
    agent any
    environment { 
        input = 'yes'
    }
    parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    }

    stages {
        stage('Build') {
            steps {
                echo "${params.Greeting} World!"
                echo 'Building..'
		bat "mvn clean"
                echo "$input"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
		bat "mvn test"
                echo ''
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
		always {
		    emailext body: 'the pipeline has been triggered successfully', subject: 'Pipeline Summary', to: '1tejeswararaonuka@gmail.com'
			echo 'pipeline has ended'
		}
	}
}
