pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
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
