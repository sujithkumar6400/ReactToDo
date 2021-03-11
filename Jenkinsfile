node {
    def app

    stage('Clone repository') { 
        checkout scm
       sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash'
       sh '. ~/.nvm/nvm.sh'
       sh 'nvm install node'
       sh 'node --version'
        sh "echo $PATH"
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