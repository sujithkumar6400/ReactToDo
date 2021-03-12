node {
    def app
    
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
         sh 'docker ls'
         sh 'docker build -f Dockerfile -t sujithkumar597/reacttodo:100 .'
         sh 'docker image push sujithkumar597/reacttodo:100 .'
    }
}