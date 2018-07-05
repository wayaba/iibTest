pipeline {
    agent {
        docker { image 'ppedraza/iibpiola:latest' 
                args '-e LICENSE=accept -e NODENAME=DesaDocker1 -e SERVERNAME=MiSERVER1'
        }
    }
	parameters {
        string(name: 'mqsi.home', defaultValue: '/opt/ibm/iib-10.0.0.10/tools', description: '')
		string(name: 'toolkit.home', defaultValue: '/opt/ibm/iib-10.0.0.10', description: '')
		string(name: 'workspaces.dir', defaultValue: '/var/jenkins_home/workspace/Pipelineando/ApiMascotas', description: '')
		string(name: 'bar.name', defaultValue: '/var/tmp/apimascotas.bar', description: '')
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
                echo "${mqsi.home}/mqsicreatebar -data ${workspaces.dir} -b ${bar.name} -o ApiMascotas/gen/ApiMascotas.msgflow"
            }
        }
		
    }
}