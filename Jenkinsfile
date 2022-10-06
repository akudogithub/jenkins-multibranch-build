pipeline{
	agent any
	stages{
		stage('1-version control'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github-id', url: 'https://github.com/akudogithub/jenkins-parallel.git']]])
			}
		}
		stage('2-code build'){
			steps{
				sh 'lscpu'
			}
		} 
	}
	stages{
		parallel{
			stage('parallel-job'){
				steps{
					sh 'lsblk'
				}
			}
			stage('sub-job-sast'){
				when{
					branch 'develop'
				}
				steps{
					sh 'id ubuntu'
				}
			}
			stage('sub-job-dast'){
				when{
					branch 'feature'
				}
				steps{
					sh 'cal'
				}
			}
		}
	}
	stages{
		stage('3-code-acceptance test'){
			steps{
				sh 'date'
			}
		}
		stage('4-code-deploy'){
			when{
				branch 'main'
			}
			steps{
				sh 'uptime'
			}
		}
		stage('5-deployment-test'){
			steps{
				sh 'sort -r /etc/passwd'
			}
		}
	}
	stages{
		parallel{
			stage('sub-job-unit-test'){
				steps{
					sh 'touch file1'
				}
			}
			stage('sub-job-final-test'){
				steps{
					sh 'mkdir buildjob1'
				}
			}
		}
	}
	stages{
		stage('6-uat'){
			steps{
				sh 'uptime'
			}
		}
		stage('prod'){
			steps{
				sh 'wc -c /etc/passwd'
			}
		}
	}
}
