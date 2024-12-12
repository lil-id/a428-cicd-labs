// This Declarative Pipeline
// pipeline {
//     agent {
//         docker {
//             image 'node:16-buster-slim' 
//             args '-p 3000:3000' 
//         }
//     }
//     stages {
//         stage('Build') { 
//             steps {
//                 sh 'npm install'
//             }
//         }
//         stage('Test') {
//             steps {
//                 sh './jenkins/scripts/test.sh'
//             }
//         }
//     }
// }

// This Scripted Pipeline
node {
    def dockerImage = 'node:16-buster-slim'
    def dockerArgs = '-p 3000:3000'

    stage('Build') {
        def dockerImageId = docker.image(dockerImage).id
        sh "docker run --rm -v ${env.WORKSPACE}:/app ${dockerImageId} /bin/sh -c 'cd /app && npm install'"
    }

    stage('Test') {
        sh "docker run --rm -v ${env.WORKSPACE}:/app ${dockerImageId} /bin/sh -c './jenkins/scripts/test.sh'"
    }
}
