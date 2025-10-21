pipeline {
 agent any
 stages {
 stage('Build') {
 steps {
 echo "Build Docker Image"
 bat "docker build -t dockerweek7nw ."
 }
 }
 stage('Run') {
 steps {
 echo "Run application in Docker Container"
 bat "docker rm -f mycontainer || exit 0"
 //forcibly removes the Docker container named mycontainer
 //If the container does not exist, this command will fail and return anerror
 //To avoid this error, exit 0, tells the shell to exit with a success status

 bat "docker run -d -p 5000:5000 --name mycontainer dockerweek7nw"
 //with -d runs the container in detached mode,
 //meaning it runs in the background, and you get your terminal back
 // immediately.
 //Without –d, app runs in the foreground, terminal shows container logsand is “blocked” by the container process.
 }
 }
 }
 post {
 success {
 echo 'Pipeline completed successfully!'
 }
 failure {
 echo 'Pipeline failed. Please check the logs.'
 }
 }
}