pipeline {
    agent any
    stages {
        stage('Install') {
            steps { 
                git url: 'https://gitlab.com/careedge/care-ui.git'
                //sh 'npm install' 
                
            }
        }
        stage('Build') {
            steps{
                sh 'npm install'  //git url: 'https://gitlab.com/careedge/care-ui.git'
                sh 'ng build --configuration production'
            }
        }
        stage('Zip Jar Files') {
            steps {
                script {
                    zip zipFile: "${env.BUILD_NUMBER}.zip", archive: false, dir: 'dist/care'
                    archiveArtifacts artifacts: "${BUILD_NUMBER}.zip", fingerprint: true
                }
            }
        }
    }
}
