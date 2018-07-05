pipeline {
    agent {
        docker { image 'ppedraza/iibpiola:latest' 
                args '-e LICENSE=accept -e NODENAME=DesaDocker1 -e SERVERNAME=MiSERVER1'
        }
    }
	parameters {
        string(name: 'mqsihome', defaultValue: '/opt/ibm/iib-10.0.0.10/tools', description: '')
		string(name: 'workspacesdir', defaultValue: '/var/jenkins_home/workspace/Pipelineando/ApiMascotas', description: '')
		string(name: 'barname', defaultValue: '/var/tmp/apimascotas.bar', description: '')
    }
    stages {
        stage('Test') {
            steps {
                sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
				sh "cat /var/jenkins_home/workspace/Pipelineando/README.md"
            }
        }
		stage('Compilacion') {
            steps {
                echo "${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -o ApiMascotas/gen/ApiMascotas.msgflow"
            }
        }
		
    }
}