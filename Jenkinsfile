node {
    def app

    environment {
        registry = "sujithkumar597/reacttodo"
        registryCredentials = 'dockerhub_id'
        dockerImage = ''
    }
    
    stage('Environment verification'){
        sh "echo $PATH"
        sh 'docker --version'
        sh 'npm --version'
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
        script {
            dockerImage = docker.build registry + ":$BUILD_NUMBER"
            docker.withRegistry( '', registryCredential ) { 
                dockerImage.push()
            }
        }
    }
}