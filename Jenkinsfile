node {
    def app

    stage('Clone repository') { 
        checkout scm
       
    }
    stage ('Install') {
        sh "echo $PATH"
         sh 'docker --version'
         sh 'sudo npm --version'
        sh 'sudo npm install'
    }

    stage ('Build') {
        sh 'sudo npm build'
    }


    stage('Build image') {
        echo "Starting Publish To Docker"
         sh 'docker build -f Dockerfile -t sujithkumar597/reacttodo:100 .'
         sh 'docker image push sujithkumar597/reacttodo:100 .'
    }
}