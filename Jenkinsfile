node {

    checkout scm

    // deploy env dev
    stage("Build") {
        docker.image('shippingdocker/php-composer:7.4').inside('-u root') {
            sh 'rm -f composer.lock'
            sh 'composer install'
        }
    }

    // Testing
    stage("Testing") {
        docker.image('ubuntu').inside('-u root') {
            sh 'echo "Ini adalah test"'
        }
    }

}
// node {

//     checkout scm

//     stage("Build") {
//         docker.image('composer:2').inside('-u root') {
//             sh 'rm -f composer.lock'
//             sh 'composer install'
//         }
//     }

//     stage("Testing") {
//         docker.image('ubuntu').inside('-u root') {
//             sh 'echo "Ini adalah test pipeline Jenkins Laravel"'
//         }
//     }

// }
// // pipeline {
// //     agent any

// //     stages {

// //         stage('Install Dependency') {
// //             steps {
// //                 script {
// //                     docker.image('composer:2').inside('--user root') {
// //                         sh 'chmod -R 777 /var/jenkins_home/workspace'
// //                         sh 'composer install --no-interaction --prefer-dist'
// //                     }
// //                 }
// //             }
// //         }

// //         stage('Laravel Check') {
// //             steps {
// //                 sh 'php -v || true'
// //                 sh 'ls -la'
// //             }
// //         }

// //         stage('Testing') {
// //             steps {
// //                 echo 'Pipeline Laravel Jenkins berhasil dijalankan'
// //             }
// //         }

// //     }
// // }
// pipeline {
//     agent any

//     stages {

//         stage('Build') {
//             steps {
//                 script {
//                     docker.image('composer:2').inside('--user root') {
//                         sh 'chmod -R 777 /var/jenkins_home/workspace'
//                         sh 'composer install --no-interaction --prefer-dist'
//                     }
//                 }
//             }
//         }

//         stage('Testing') {
//             steps {
//                 script {
//                     docker.image('ubuntu').inside {
//                         sh 'echo "Ini adalah test pipeline Jenkins Laravel"'
//                     }
//                 }
//             }
//         }

//     }
// }
// // pipeline {
// //     agent any

// //     stages {

// //         stage('Build') {
// //             steps {
// //                 script {
// //                     docker.image('composer:2').inside {
// //                         sh 'git config --global --add safe.directory "*"'
// //                         sh 'composer install --prefer-dist --no-progress --no-interaction'
// //                     }
// //                 }
// //             }
// //         }

// //         stage('Testing') {
// //             steps {
// //                 sh 'echo "Ini adalah test pipeline Jenkins Laravel"'
// //             }
// //         }

// //         stage('Deploy') {
// //             steps {
// //                 sshagent(['ssh-prod']) {
// //                     sh '''
// //                     ssh -o StrictHostKeyChecking=no root@172.28.167.7 "cd /var/www && git pull origin main"
// //                     '''
// //                 }
// //             }
// //         }

// //     }
// // }
// // pipeline {
// //     agent any

// //     stages {

// //         stage('Build') {
// //             steps {
// //                 sh 'composer install'
// //             }
// //         }

// //         stage('Deploy') {
// //             steps {
// //                 sshagent(['ssh-prod']) {
// //                     sh '''
// //                     ssh -o StrictHostKeyChecking=no root@172.28.167.7 "cd /var/www && git pull origin main"
// //                     '''
// //                 }
// //             }
// //         }

// //     }
// // }
