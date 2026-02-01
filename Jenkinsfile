node {
    // 환경 변수를 1.43으로 고정합니다.
    withEnv(['DOCKER_API_VERSION=1.43']) {
        stage('Clone repository') {
            git branch: 'main', 
                credentialsId: 'github_access_token', 
                url: 'https://github.com/Format91/web-count.git'
        }

        stage('Build image') {
            dockerImage = docker.build("format39/web_count:1.0")
        }

        stage('Push image') {
            withDockerRegistry([ credentialsId: "docker-access", url: "" ]) {
                dockerImage.push()
            }
        }
    }
}