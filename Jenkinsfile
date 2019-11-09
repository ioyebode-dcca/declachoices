pipeline {
	agent any

	parameters {
      choice(
	      name: 'PATCH_ENV',
        choices: ['dev', 'test', 'impl', 'prd', 'devops'],
	      description: 'Enter Environment to patch')
  }


	stages {
		stage ('one') {
			steps {
			checkout scm
			}
		}
		stage ('two') {
			steps {
				input('Do you want to proceed?')
			}
		}

		stage ('parameters') {
		    choice(
			name: 'PATCH_ENV',
			choices: ['dev', 'test', 'impl'],
			description: 'Enter Environment to patch')
		}

		stage ('three') {
			steps {
			echo 'Staging area verified'
			}

		}
		stage ('four') {
			steps {
			echo 'successful!'
			}
		}
		stage('verify tools') {
			parallel {
				stage('Verify Git') {
					steps {
					sh 'git --version'
					}
				}
				stage('maven verify') {
					steps {
					echo 'mvn -v'
					}
				}

				stage('ansible verify') {
				    steps {
					sh 'ansible --version'
					}
				}
				stage('Junit Test') {
					steps {
					echo 'performing Junit test'
					}
				}
				stage('Selenium Test') {
					steps {
					echo 'performing Selenium testing'
					}
				}
				stage('UFT TESTING') {
					steps {
					echo 'uft successfully'
					}
				}
			}
		}
		stage ('five') {
			steps {
				input('Is test deployment okay?')
			}
		}
		stage ('Check system runtime') {
			steps {
			sh 'uptime'
			sh 'env'
			}
		}

	}
}
