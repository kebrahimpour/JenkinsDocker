pipeline {
	agent any
	stages {
		
			stage('SCM'){
				steps {
					checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/FeynmanFan/JenkinsDocker']]])
				}
			}
			stage('Build'){
				steps {
					try{
						sh 'dotnet build ConsoleApp1'
					}
					finally{
						archiveArtifacts artifacts: 'ConsoleApp1/*.*'
					}
				}
			}
			stage('Test'){
				steps {
					echo 'Execute unit tests'
				}
			}
			stage('Package'){
				steps {
					echo 'Zip it up'
				}
			}
			stage('Deploy'){
				steps{
					echo 'Push to deployment'
				}
			}
			stage('Archive'){
				steps {
					archiveArtifacts artifacts: 'ConsoleApp1/*.*'
				}
			}
	}
	
}
