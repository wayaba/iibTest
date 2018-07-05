pipeline {
    agent {
        docker { image 'ppedraza/iibpiola:latest' 
                args '-e LICENSE=accept -e NODENAME=DesaDocker1 -e SERVERNAME=MiSERVER1'
        }
    }
    stages {
        stage('Test') {
            steps {
                sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
				sh "cat /var/jenkins_home/workspace/Pipelineando/README.md"
            }
        }
    }
}