pipeline {
    agent {
        docker { image 'ppedraza/iibpiola:latest' 
                args '-e LICENSE=accept -e NODENAME=DesaDocker1 -e SERVERNAME=MiSERVER1 -v /var/jenkins_home/workspace/iib:/opt/ibm/iib-10.0.0.10/server/bin'
        }
    }
	parameters {
        string(name: 'mqsihome', defaultValue: '/opt/ibm/iib-10.0.0.10/tools', description: '')
		string(name: 'workspacesdir', defaultValue: '/var/jenkins_home/workspace/Pipelineando', description: '')
		string(name: 'barname', defaultValue: '/var/tmp/apimascotas.bar', description: '')
		string(name: 'appname', defaultValue: 'ApiMascotas', description: '')
    }
    stages {
        stage('Test') {
            steps {
                sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
				sh "cat /var/jenkins_home/workspace/Pipelineando/README.md"
            }
        }
		/*
		stage('SonarQube') {
		
			steps {
				script {
					// requires SonarQube Scanner 2.8+
					scannerHome = tool 'sonnar-jenkins'
				}
				withSonarQubeEnv('sonnar-jenkins') {
					sh "${scannerHome}/bin/sonar-scanner"
				}
			}
        }
		*/
		
		stage('Compilacion') {
            steps {
				echo "Quien soy: "
				sh "whoami"
				echo "Seteo el environment"
				
				dir("/opt/ibm/iib-10.0.0.10/server/bin") {
				
                    //sh "pwd"
					//echo "puto"
					//sh "ls -l"
					sh " . ./mqsiprofile"
                }
				
				//sh "sudo /opt/ibm/iib-10.0.0.10/server/bin . ./mqsiprofile"
				//sh " . ./opt/ibm/iib-10.0.0.10/server/bin/mqsiprofile"
				echo "EJECUTO ${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -a ${params.appname}"
				sh "${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -a ${params.appname}"
            }
			
        }
		
		
		
    }
}