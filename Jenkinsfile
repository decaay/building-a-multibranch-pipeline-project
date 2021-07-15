pipeline {
    agent any

    parameters {
        string(name: 'REGISTRY_URL', defaultValue: 'registry.hub.docker.com', description: 'URL of registry')
        string(name: 'CREDENTIALS_ID', defaultValue: 'docker-creds', description: 'credentials for docker login')
        string(name: 'LOCAL_IMAGE_NAME', defaultValue: 'test', description: 'local image path')
    }

    stages {
        stage('copyBuild') {
            steps {
                script {
                    
                    docker.withRegistry("${REGISTRY_URL}", "${CREDENTIALS_ID}") {
                        build_image = docker.image("${LOCAL_IMAGE_NAME}")
                        build_image.push()
                    }
                }
            }
        }
    }
}
