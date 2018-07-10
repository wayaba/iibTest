#!/usr/bin/env groovy

node {
    stage('checkout') {
        checkout scm
    }

    docker.image('ppedraza/iibpiola:latest').inside('-u root -e "LICENSE=accept" -e "NODENAME=DesaDocker1" -e "SERVERNAME=MiSERVER1"') {
        stage('adentro') {
            echo "A ver..."
			sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
			echo "A ver gas..."
			sh "sudo /opt/ibm/iib-10.0.0.10/server/bin . ./mqsiprofile"
        }

        

    }

}