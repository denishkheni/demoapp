node {
    def app

    stage('Clone repository') {
        /* repository cloned to our workspace */

        checkout scm
    }
    
  
    
    stage('Build image') {
        /* To builds the dockerimage */
        //update your ECR registry URI
        app = docker.build("https://050455579260.dkr.ecr.us-east-1.amazonaws.com/tokigamesdemo")
    }

    stage('Test image') {
        /* Try killing some white walkers for testing ;-) */

        app.inside {
            sh 'echo "Hurray !! Tests passed, Valar Morghulis "'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image */
        //docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
        // update your ECR registry URI and jenkins crendential paramater
        docker.withRegistry('https://050455579260.dkr.ecr.us-east-1.amazonaws.com/tokigamesdemo', 'ecr:us-east-1:aws_ecr')    {
            //app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
