pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: 'Node 6.x', configId: '<config-file-provider-id>') {
                    sh 'npm config ls'
                }
            }
        }
    }
}

// node {
//     def app

//     stage('Clone repository') { 
//         checkout scm
       
//     }
//     stage ('Install') {
//          sh 'docker --version'
//          sh 'npm --version'
//         sh 'npm install'
//     }

//     stage ('Build') {
//         sh 'npm build'
//     }


//     stage('Build image') {
//         echo "Starting Publish To Docker"
//          sh 'docker build -f Dockerfile -t sujithkumar597/reacttodo:100 .'
//          sh 'docker image push sujithkumar597/reacttodo:100 .'
//     }
// }