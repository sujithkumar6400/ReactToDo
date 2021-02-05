node {
    def app

    stage('Clone repository') {  

        checkout scm
    }
    stage ('Install') {
        sh 'apt-get update && apt-get install nodejs'
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
}