node {
    def app

    stage('Clone repository') {  

        checkout scm
    }

    stage ('Install') {
		sh 'curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -'
        sh 'echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list'
        sh 'apt-get update && apt-get install yarn'
        sh 'cat /home/jenkins/npmrc/.npmrc > ~/.npmrc'
        sh 'curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -'
        sh 'apt-get update && apt-get install nodejs'
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

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'git') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}