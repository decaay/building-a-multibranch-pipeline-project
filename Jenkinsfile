pipeline {
    agent any

    parameters {
        string(name: 'REGISTRY_URL', defaultValue: 'registry.hub.docker.com', description: 'URL of registry')
        string(name: 'USER_NAME', defaultValue: 'admin', description: 'registry user name')
        string(name: 'CREDENTIALS_ID', defaultValue: 'docker-creds', description: 'credentials for docker login')
    }

    stages {
        stage('copyBuild') {
            steps {
                script {
                    //build_image = docker.image('dkadam07/mytest')
                    docker.withRegistry("docker.io", "docker-creds") {
                        //sh "docker push dkadam07/mytest:latest"
                        sh 'echo "Hello world!"'
                    }
                }
            }
        }
    }
}

// def pushToRegistry(String registryUrl, String userName, String password, String localImagePath,String registryImagePath) {
//     sh(label: "docker login", script: "docker login -u ${userName} -p ${password} ${registryUrl}")
//     sh(label: "docker tag", script: "docker tag ${localImagePath} ${registryImagePath}")
//     sh(label: "docker push", script: "docker push ${registryImagePath}")
//     sh(label: "docker logout", script: "docker logout ${registryUrl}")
// }