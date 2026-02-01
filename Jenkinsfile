node {
    stage('Clone repository') {
        git branch: 'main',
        git credentialsId: 'github_access_token', url: 'https://github.com/Format91/web-count.git'
    }

    stage('Build image') {
       dockerImage = docker.build("format39/web_count:v1.0")
    }

    stage('Push image') {
        withDockerRegistry([ credentialsId: "docker-access", url: "" ]) {
        dockerImage.push()
        }
    }
}
