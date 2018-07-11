#!/bin/bash
pipeline {
/*
	agent {
        docker { image 'ppedraza/iibpiola:latest' 
                args '-u 0:0 -e LICENSE=accept -e NODENAME=DesaDocker1 -e SERVERNAME=MiSERVER1'
        }
    }
*/
agent any
	environment {
		DISPLAY = ":1"
	}
	
	parameters {
        string(name: 'mqsihome', defaultValue: '/opt/ibm/iib-10.0.0.10/tools', description: '')
		string(name: 'workspacesdir', defaultValue: '/var/jenkins_home/workspace/Pipelineando', description: '')
		string(name: 'barname', defaultValue: '/var/jenkins_home/workspace/bar/apimascotas.bar', description: '')
		string(name: 'appname', defaultValue: 'ApiMascotas', description: '')
    }

	stages {
	
		stage('SonarQube analysis') {
			steps {
				script {
					def scannerHome = tool 'sonnar-jenkins'
					withSonarQubeEnv('sonarqube') {
						sh "${scannerHome}/bin/sonar-scanner \
										-Dsonar.projectKey=esqpipeline \
										-Dsonar.projectname=Esqpipeline \
										-Dsonar.projectVersion=1 \
										-Dsonar.sources=. \
										-Dsonar.language=esql"
					}
				}
			}
		}
		
		stage('set environment')
			{
				steps{
						echo "A ver..."
						sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
						echo "A ver gas..."
						sh '''
							sudo Xvfb :1 -screen 0 1024x768x24 </dev/null &
							export DISPLAY=":1"
						'''
					}
					
			}
		
		
		stage('Compilacion') {
				steps {
					echo "EJECUTO ${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -a ${params.appname}"
					sh "${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -a ${params.appname} -skipWSErrorCheck"
				}
				
			}
	}
}