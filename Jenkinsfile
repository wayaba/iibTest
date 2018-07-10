#!/bin/bash -xe

node {

	sh "#!/bin/ksh \n" +
       "echo \"Hello from \$SHELL\""
    

    docker.image('ppedraza/iibpiola:latest').inside('-u 0:0 -e "LICENSE=accept" -e "NODENAME=DesaDocker1" -e "SERVERNAME=MiSERVER1"') {
        stage('adentro') {
            echo "A ver..."
			sh "cat /opt/ibm/iib-10.0.0.10/tools/eclipse.ini"
			sh "whoami"
			echo "A ver gas..."
			sh ". /opt/ibm/iib-10.0.0.10/server/bin/mqsiprofile"
        }

        

    }

}