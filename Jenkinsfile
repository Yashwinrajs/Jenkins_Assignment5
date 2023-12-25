pipeline {

agent none

parameters {
  choice choices: ['dev', 'qa'], name: 'Environment'
  string defaultValue: 'Yashwinraj', name: 'name'
}

environment {
  env = "${params.Environment}"
  user = "${params.name}"
}

	stages {
  		stage('stage1') {
				agent { label 'Agent-Sonar' }
    				steps {
      					sh 'echo "Hi This is ${user}"'
					sh 'echo "Build URL: ${BUILD_URL}"'
    					}
  				}
		stage('stage2') {
				agent { label 'Agent-Sonar' }
    				steps {
      					sh 'echo "Deployment Environment: ${env}"'
					sh 'echo "Jenkins URL: ${JENKINS_URL}"'
    					}
  				}

  		stage('stage3') {
				when {
				allOf {
                		expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
				}
            			}
				agent { label 'Agent-Tomcat' }
    				steps {
      					sh 'echo "Branch Name: ${BRANCH_NAME}"'
    				}
  				}
    		stage('stage4') {
				when {
                		expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
            			}
				agent { label 'Agent-Tomcat' }
    				steps {
      					sh 'echo "Build ID: ${BUILD_ID}"'
					build 'demo-Fifth'
    					}
				}
	
	}
	
}
