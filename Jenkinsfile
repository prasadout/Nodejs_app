node {
    def app

    stage('Clone repository') {
        
        checkout scm
    }

    stage('Build image') {
        
        app = docker.build("nani1011/helloworld")
    }


    stage('Push image') {
        docker.withRegistry('https://hub.docker.com/', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }

    }
}

