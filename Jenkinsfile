pipeline {
    agent any

 
    stages {
          

	stage('gcloud auth') {
            steps {
                
                withCredentials([file(credentialsId: 'JENKINS-ID', variable: 'JENKINS_KEY_FILE')]) {
				  sh """
                                        gcloud version
					gcloud auth activate-service-account --key-file="$JENKINS_KEY_FILE"
					gcloud compute instances create my-app-instance-automation --project=my-project-279-436907 --zone=us-central1-f --machine-type=e2-medium --metadata-from-file=startup-script=./startup-script.sh
          gcloud compute firewall-rules create default-allow-http-80 --allow tcp:80 --source-ranges 0.0.0.0/0 --target-tags http-server --description "Allow port 80 access to http-server"
				  """
				}
        }
	    }
		}
		}
