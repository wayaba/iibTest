#!/bin/bash
node {
	

    docker.image('ppedraza/iibpiola:latest').inside('-u 0:0 -e "LICENSE=accept" -e "NODENAME=DesaDocker1" -e "SERVERNAME=MiSERVER1"') {
        stage('adentro') {
            echo "A ver..."
			//sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
			sh "whoami"
			echo "A ver gas..."
			echo "probando..."
			//sh ". /opt/ibm/iib-10.0.0.10/server/bin/mqsiprofile"
        }
		
		stage('hola'){
			echo "EJECUTO ${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -a ${params.appname}"
			sh "${params.mqsihome}/mqsicreatebar -data ${params.workspacesdir} -b ${params.barname} -a ${params.appname}"
		}

        

    }

}