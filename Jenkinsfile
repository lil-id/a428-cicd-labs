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
    // Use docker image equivalent in scripted pipeline
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
        stage('Build') {
            // Checkout SCM is typically added in scripted pipelines
            checkout scm
            
            // Equivalent to npm install step
            sh 'npm install'
        }
        
        stage('Test') {
            // Equivalent to test script execution
            sh './jenkins/scripts/test.sh'
        }
    }
}
