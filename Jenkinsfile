pipeline {
    agent any
    stages {
        stage('Tests') {
            steps {
//                 script {
//                    docker.image('node:10-stretch').inside { c ->
                        echo 'Building..'
                        sh 'npm install'
                        echo 'Testing..'
                        sh 'npm test'
//                         sh "docker logs ${c.id}"
//                    }
//                 }
            }
        }
	stage('Build and push docker image') {
            steps {
                script {
                    def dockerImage = docker.build("anandkoligudda/node-demo:master")
                    docker.withRegistry('', 'docker') {
                        dockerImage.push('master')
                    }
                }
            }
        }

    }
}
