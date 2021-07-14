pipeline {
    agent any

    parameters {
        string(name: 'REGISTRY_URL', defaultValue: 'https://registry.hub.docker.com', description: 'URL of registry')
        string(name: 'USER_NAME', defaultValue: 'admin', description: 'registry user name')
        string(name: 'CREDENTIALS_ID', defaultValue: 'docker-creds', description: 'credentials for docker login')
    }

    stages {
        stage('copyBuild') {
            steps {
                sh 'echo "Hello world!"'
                //sh(label: "docker build", script: "docker build -t $LOCAL_DOCKER_IMAGE .")
                build_image = docker.image('dkadam07/mytest')
                docker.withRegistry(params.REGISTRY_URL, params.CREDENTIALS_ID) {
                    build_image.push()
                }
                // pushToRegistry(ODYSSEY_DOCKER_REGISTRY, ODYSSEY_DOCKER_CREDS_USR, ODYSSEY_DOCKER_CREDS_PSW,
                //     LOCAL_DOCKER_IMAGE, "$ODYSSEY_DOCKER_REGISTRY/$REMOTE_DOCKER_IMAGE:$BUILD_ID" )
                // sh(label: "remove local image", script: "docker rmi ${LOCAL_DOCKER_IMAGE}")
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