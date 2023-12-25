pipeline {

agent {
  label 'Agent-Sonar'
	}

parameters {
  choice choices: ['dev', 'qa'], name: 'Environment'
  string defaultValue: 'Yashwinraj', name: 'name'
}

environment {
  env = "$Environment"
  user = "$name"
}

	stages {
  		stage('stage1') {
    				steps {
      					sh 'echo "Hi This is ${user}"'
					sh 'echo "Build URL: ${BUILD_URL}"'
    					}
  				}
		stage('stage2') {
    				steps {
      					sh 'echo "Deployment Environment: ${env}"'
					sh 'echo "Jenkins URL: ${JENKINS_URL}"'
    					}
  				}
  		stage('stage3') {
    				steps {
      					sh 'echo "Branch Name: ${BRANCH_NAME}"'
    					}
  				}
	post {
  	success {
    		stage('stage4') {
    				steps {
      					sh 'echo "Build ID: ${BUILD_ID}"'
    					}
  				}
  		}
		}

	}
	
}
