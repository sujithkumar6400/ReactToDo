node {
    def app

    stage('Clone repository') {  

        checkout scm
    }

    stage ('Install NPM') {
		
        sh 'apt-get update && apt-get install nodejs'
    }

    stage ('Install') {
        sh 'npm install'
    }

    stage ('Build') {
        sh 'npm build'
    }


    stage('Build image') {
        echo "Starting Publish To Docker"
         sh 'docker build -f Dockerfile -t sujithkumar597/reacttodo:2 .'
         sh 'docker image push sujithkumar597/reacttodo:2 .'
    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'git') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}