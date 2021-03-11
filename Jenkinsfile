node {
    def app

    env.NODEJS_HOME = "${tool 'Node 6.x'}"
    // on linux / mac
    env.PATH="${env.NODEJS_HOME}/bin:${env.PATH}"
    
    sh 'npm --version'

    stage('Clone repository') { 
        checkout scm
       
    }
    stage ('Install') {
        sh "echo $PATH"
        sh 'cat /home/jenkins/npmrc/.npmrc > ~/.npmrc'
        sh 'npm cache clean -f'
         sh 'docker --version'
         sh 'npm --version'
        sh 'npm install'
    }

    stage ('Build') {
        sh 'npm build'
    }


    stage('Build image') {
        echo "Starting Publish To Docker"
         sh 'docker build -f Dockerfile -t sujithkumar597/reacttodo:100 .'
         sh 'docker image push sujithkumar597/reacttodo:100 .'
    }
}