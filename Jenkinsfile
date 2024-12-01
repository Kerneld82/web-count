node {
    stage('Clone repository') {
        echo 'Starting to clone the repository...'
        git credentialsId: 'github_access_token', url: 'https://github.com/Kerneld82/web-count.git'
        echo 'Repository cloned successfully.'
    }

    stage('Build image') {
        echo 'Starting to build the Docker image...'
        dockerImage = docker.build("jjam943/web_count:v1.0")
        echo 'Docker image built successfully.'
    }

    stage('Push image') {
        echo 'Starting to push the Docker image...'
        withDockerRegistry([ credentialsId: "docker-access", url: "" ]) {
            dockerImage.push()
        }
        echo 'Docker image pushed successfully.'
    }
}
