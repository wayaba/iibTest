#!/bin/bash
pipeline {

	parameters {
        string(name: 'mqsihome', defaultValue: '/opt/ibm/iib-10.0.0.10/tools', description: '')
		string(name: 'workspacesdir', defaultValue: '/var/jenkins_home/workspace/Pipelineando', description: '')
		string(name: 'barname', defaultValue: '/var/tmp/apimascotas.bar', description: '')
		string(name: 'appname', defaultValue: 'ApiMascotas', description: '')
    }

	stages {
		stage('set environment')
			{
				steps{
					def img = docker.image('ppedraza/iibpiola:latest').withRun('-u 0:0-e LICENSE=accept -e NODENAME=DesaDocker1 -e SERVERNAME=MiSERVER1');
					img.inside {
						echo "A ver..."
						sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
						echo "A ver gas..."
					}
					
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