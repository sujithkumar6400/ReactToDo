node ('node-npm') {
    
    stage('Clone repository') {  

        checkout scm
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
}