pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Pastikan URL Git benar dan tanpa spasi
                git url: 'https://github.com/nurlayla-06/node-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test' // pastikan ada script "test" di package.json
            }
        }

        stage('Deploy') {
            steps {
                echo 'Menjalankan aplikasi...'
                sh 'nohup node app.js > output.log 2>&1 &'
            }
        }
    }

    post {
        success {
            echo 'Pipeline selesai dengan sukses!'
        }
        failure {
            echo 'Pipeline gagal pada salah satu tahap.'
        }
    }
}
