#!/bin/bash
node {
	

    docker.image('ppedraza/iibpiola:latest').inside('-u 0:0 -e "LICENSE=accept" -e "NODENAME=DesaDocker1" -e "SERVERNAME=MiSERVER1"') {
        stage('adentro') {
            echo "A ver..."
			sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
			sh "whoami"
			echo "A ver gas..."
			sh "bash"
			sh ". /opt/ibm/iib-10.0.0.10/server/bin/mqsiprofile"
        }

        

    }

}