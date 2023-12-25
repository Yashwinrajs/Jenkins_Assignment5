pipeline {

parameters {
  choice choices: ['dev', 'qa'], name: 'Environment'
  string defaultValue: 'Yashwinraj', name: 'name'
}

environment {
  env = "${Environment}"
  user = "${name}"
	}

agent {
  label 'Agent-Sonar'
	stages {
  		stage('stage1') {
    				steps {
      					sh 'echo "Hi This is $user"'
					sh 'echo "Build URL: ${BUILD_URL}"'
    					}
  				}
		stage('stage2') {
    				steps {
      					sh 'echo "Deployment Environment: ${env}"'
					sh 'echo "Jenkins URL: ${JENKINS_URL}"'
    					}
  				}

				}

		}

	}


post {
  success {
    
agent {
  label 'Agent-Tomcat'
	stages {
  		stage('stage3') {
					when {
  						branch 'main* dev* '
						}
    				steps {
      					echo "Branch Name: ${BRANCH_NAME}"
    					}
  				}
	post {
  	success {
    		stage('stage4') {
    				steps {
      					echo "Build ID: ${BUILD_ID}"
    					}
  				}
  		}
	}

		}

	}
  }
}
