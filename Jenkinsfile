node {

    checkout scm

    stage("Build") {
        withEnv(['DOCKER_HOST=unix:///var/run/docker.sock']) {
            docker.image('shippingdocker/php-composer:7.4').inside('-u root') {
                sh 'rm -f composer.lock'
                sh 'composer install'
            }
        }
    }

    stage("Testing") {
        withEnv(['DOCKER_HOST=unix:///var/run/docker.sock']) {
            docker.image('ubuntu').inside('-u root') {
                sh 'echo "Ini adalah test pipeline Jenkins Laravel"'
            }
        }
    }

}
