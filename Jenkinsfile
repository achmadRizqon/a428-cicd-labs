// pipeline {
//     agent any

//     environment {
//         NODE_OPTIONS = '--openssl-legacy-provider'
//     }

//     stages {
//         stage('Install Dependencies') {
//             steps {
//                 sh 'npm install'
//             }
//         }

//         stage('Build') {
//             steps {
//                 sh 'npm run build'
//             }
//         }

//         stage('Test') {
//             steps {
//                 sh './jenkins/scripts/test.sh'
//             }
//         }
//     }
// }

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

node {
    stage('Clone') {
        git branch: 'react-app', url: 'https://github.com/achmadRizqon/a428-cicd-labs.git'
    }

    stage('Build') {
        sh 'docker run --rm -v $PWD:/app -w /app node:lts-buster-slim npm install'
    }

    stage('Test') {
        sh 'docker run --rm -v $PWD:/app -w /app node:lts-buster-slim npm test -- --watchAll=false'
    }
}