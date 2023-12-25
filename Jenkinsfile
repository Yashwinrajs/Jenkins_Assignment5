pipeline {

agent {
  label 'Agent-Sonar'
	}

parameters {
  choice choices: ['dev', 'qa'], name: 'Environment'
  string defaultValue: 'Yashwinraj', name: 'name'
}

environment {
  env = '${Environment}'
  user = '${name}'
}
	
	stages {
  		stage('stage1') {
    				steps {
      					sh 'echo "Hi This is $user"'
					sh 'echo "${BUILD_URL}"'
    					}
  				}
		stage('stage2') {
    				steps {
      					sh 'echo "Deployment Environment: ${env}"'
					sh 'echo "${JENKINS_URL}"'
    					}
  				}

		}

}
