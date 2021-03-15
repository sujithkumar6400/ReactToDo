node {
    def app
    
    stage('Environment verification'){
        sh "echo $PATH"
        sh 'docker --version'
        sh 'npm --version'
        sh 'npm cache clean -f'
    }

    stage('Clone repository') { 
        checkout scm
       
        sh "echo $PATH"
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
        app.inside {
            sh 'echo "Tests passed"'
        }
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