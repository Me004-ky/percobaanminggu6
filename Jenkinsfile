node {

    checkout scm

    stage("Build") {
        docker.image('composer:2').inside('-u root') {
            sh 'rm -f composer.lock'
            sh 'composer install'
        }
    }

    stage("Testing") {
        docker.image('ubuntu').inside('-u root') {
            sh 'echo "Ini adalah test pipeline Jenkins Laravel"'
        }
    }

}
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                script {
                    docker.image('composer:2').inside {
                        sh 'git config --global --add safe.directory "*"'
                        sh 'composer install --prefer-dist --no-progress --no-interaction'
                    }
                }
            }
        }

        stage('Testing') {
            steps {
                sh 'echo "Ini adalah test pipeline Jenkins Laravel"'
            }
        }

        stage('Deploy') {
            steps {
                sshagent(['ssh-prod']) {
                    sh '''
                    ssh -o StrictHostKeyChecking=no root@172.28.167.7 "cd /var/www && git pull origin main"
                    '''
                }
            }
        }

    }
}
// pipeline {
//     agent any

//     stages {

//         stage('Build') {
//             steps {
//                 sh 'composer install'
//             }
//         }

//         stage('Deploy') {
//             steps {
//                 sshagent(['ssh-prod']) {
//                     sh '''
//                     ssh -o StrictHostKeyChecking=no root@172.28.167.7 "cd /var/www && git pull origin main"
//                     '''
//                 }
//             }
//         }

//     }
// }
