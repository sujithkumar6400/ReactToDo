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
        sh 'docker build -f Dockerfile -t sujithkumar597/reacttodo:${BUILD_NUMBER} .' 
        sh 'docker image push sujithkumar597/reacttodo:${BUILD_NUMBER}'
    }

    post { 
        always { 
            cleanWs()
        }
    }
}