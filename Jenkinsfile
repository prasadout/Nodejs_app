node {
    def app

    stage('Clone repository') {
        
        checkout scm
    }

    stage('Build image') {
        
        app = docker.build("nani1011/helloworld")
    }


    stage('Push image') {
        docker.withRegistry('nani1010/nani', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }

    }
}

