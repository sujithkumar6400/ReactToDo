node {
    def app
    
    stage('Environment verification'){
        sh 'docker --version'
        sh 'echo $PATH'
        sh 'npm --version'
        sh 'npm cache clean -f'
    }

    stage('Clone repository') { 
        checkout scm
    }
    stage ('Install') {
        sh 'npm install'
    }

    stage ('Build') {
        sh 'npm run build'
    }


    stage('Build image') {
        echo "Starting Publish To Docker"
        app = docker.build("sujithkumar597/reacttodo")
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_id') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }

    post { 
        always { 
            cleanWs()
        }
    }
}