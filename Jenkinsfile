pipeline {
    agent any
    environment {
	      MY_PET = 'peppa'
	      ANOTHER_PET = 'plants'
    }
    parameters {
	string(name: 'PERSON', defaultValue: 'Archana Chillala', description: 'The person who's writing this piece of code")
    }
    stages {
        stage('build') {
		    steps {
                	sh 'echo "Hello World"'
                	sh '''
                    	echo "Multiline shell steps works too"
                    	ls -lah
               		 '''
            	}
        }
	stage('Test Parameters') {
		steps {
			echo "Hello ${params.PERSON}"
		}
	}
	stage('Sanity Check') {
		steps {
			input "Do you want to continue?"
		}
	}
	stage('Show Env Vars') {
		steps {
			sh 'echo $MY_PET'
			sh 'echo $ANOTHER_PET'
		}
	}
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}


