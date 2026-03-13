node {

    checkout scm

    // ======================
    // Build (Composer Install)
    // ======================
    stage("Build") {
        docker.image('composer:2').inside('--entrypoint="" -u root') {
            sh '''
            git config --global --add safe.directory $WORKSPACE
            rm -f composer.lock
            composer install --no-interaction --prefer-dist
            '''
        }
    }

    // ======================
    // Testing
    // ======================
    stage("Testing") {
        docker.image('php:8.3-cli').inside('-u root') {
            sh '''
            echo "Ini adalah test"
            php -v
            '''
        }
    }

    // ======================
    // Deploy ke Production
    // ======================
    stage("Deploy") {
        docker.image('agung3wi/alpine-rsync:1.1').inside('--entrypoint="" -u root') {

            sshagent(['ssh-prod']) {

                sh '''
                mkdir -p ~/.ssh
                chmod 700 ~/.ssh
                ssh-keyscan -H $PROD_HOST >> ~/.ssh/known_hosts
                '''

                sh '''
                rsync -avz --delete ./ \
                mine@$PROD_HOST:/home/mine/prod.kelasdevops.xyz/ \
                --exclude=.env \
                --exclude=storage \
                --exclude=.git
                '''
            }
        }
    }

}
// node {

//     checkout scm

//     // ======================
//     // Build (Composer Install)
//     // ======================
//     stage("Build") {
//         docker.image('composer:2').inside('-u root') {
//             sh '''
//             git config --global --add safe.directory /var/jenkins_home/workspace/laravel-dev
//             rm -f composer.lock
//             composer install --no-interaction --prefer-dist
//             '''
//         }
//     }

//     // ======================
//     // Testing
//     // ======================
//     stage("Testing") {
//         docker.image('ubuntu').inside('-u root') {
//             sh '''
//             echo "Ini adalah test"
//             php -v || true
//             '''
//         }
//     }

    // ======================
    // Deploy ke Production
    // ======================
    stage("Deploy") {
        docker.image('agung3wi/alpine-rsync:1.1').inside('-u root') {

            sshagent(credentials: ['ssh-prod']) {

                sh '''
                mkdir -p ~/.ssh
                ssh-keyscan -H $PROD_HOST >> ~/.ssh/known_hosts
                '''

                sh '''
                rsync -rav --delete ./ \
                mine@$PROD_HOST:/home/mine/prod.kelasdevops.xyz/ \
                --exclude=.env \
                --exclude=storage \
                --exclude=.git
                '''
            }
        }
    }

}
// node {

//     checkout scm

//     // deploy env dev
//     stage("Build") {
//         docker.image('composer:2').inside('-u root') {
//             sh 'rm -f composer.lock'
//             git config --global --add safe.directory /var/jenkins_home/workspace/laravel-dev
//             sh 'composer install'
//         }
//     }

//     // Testing
//     stage("Testing") {
//         docker.image('ubuntu').inside('-u root') {
//             sh 'echo "Ini adalah test"'
//         }
//     }
//     // deploy env prod
// stage("Deploy") {
//     docker.image('agung3wi/alpine-rsync:1.1').inside('-u root') {

//         sshagent (credentials: ['ssh-prod']) {

//             sh 'mkdir -p ~/.ssh'
//             sh 'ssh-keyscan -H "$PROD_HOST" > ~/.ssh/known_hosts'

//             sh """
//             rsync -rav --delete ./laravel/ \
//             ubuntu@$PROD_HOST:/home/ubuntu/prod.kelasdevops.xyz/ \
//             --exclude=.env --exclude=storage --exclude=.git
//             """
//         }

//     }
// }
// }
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
