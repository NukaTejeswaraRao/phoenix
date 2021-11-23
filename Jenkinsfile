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
                echo "$input"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
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
