pipeline {
	/*
    agent {
        docker { image 'ppedraza/iibpiola:latest' 
                args '-e LICENSE=accept -e NODENAME=DesaDocker1 -e SERVERNAME=MiSERVER1'
        }
    }
	*/
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
				def img = docker.image('ppedraza/iibpiola:latest').withRun('-e LICENSE=accept -e NODENAME=DesaDocker1 -e SERVERNAME=MiSERVER1')
				img.inside {
					echo "A ver..."
					sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
					echo "A ver gas..."
				}
				
				
				
			}
			/*
				echo "Me paro en el directorio para setear el profile"
				dir("/opt/ibm/iib-10.0.0.10/server/bin") {
					echo "Seteo profile"
					sh " . ./mqsiprofile"
					echo "profile seteado"
                }
				*/
		}
		
		stage('Compilacion') {
            steps {
				//sh "sudo /opt/ibm/iib-10.0.0.10/server/bin . ./mqsiprofile"
				//sh " . ./opt/ibm/iib-10.0.0.10/server/bin/mqsiprofile"
				echo "EJECUTO ${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -a ${params.appname}"
				sh "${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -a ${params.appname}"
            }
			
        }
		
		
		
    }
}