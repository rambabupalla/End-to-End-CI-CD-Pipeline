pipeline {
    agent { 
        label 'jslave' 
    }

    environment {    
        DOCKERHUB_CREDENTIALS = credentials('dockerlogin')
    }

    stages {

        stage('SCM_Checkout') {
            steps {
                echo "Perform SCM Checkout"
                git 'https://github.com/rambabupalla/java-mvn-springbootapp.git'
            }
        }

        stage('Application Build') {
            steps {
                echo "Perform Application Build"
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker version'
                sh "docker build -t ram8243/static-web-app:${BUILD_NUMBER} ."
                sh 'docker image list'
                sh "docker tag ram8243/static-web-app:${BUILD_NUMBER} ram8243/static-web-app:java"
            }
        }

        stage('Login2DockerHub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('Publish_to_Docker_Registry') {
            steps {
                sh "docker push ram8243/static-web-app:latest"
            }
        }

        stage('Deploy to Kubernetes Cluster') {
            steps {
                script {
                    sshPublisher(publishers: [sshPublisherDesc(configName: 'Kubernetes-Master', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'kubectl apply -f kubedeploy.yaml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '*.yaml')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                }
            }
        }

    }
}
