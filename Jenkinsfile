pipeline {
    agent any  // Gunakan host Jenkins, bukan container docker

    environment {
        NODE_ENV = 'development'
    }

    stages {
        stage('Checkout') {
            steps {
                echo '🔄 Clone repository dari GitHub...'
                git url: 'https://github.com/nurlayla-06/node-app.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo '📦 Install dependencies via npm...'
                sh 'npm install'
            }
        }

        stage('Lint (Opsional)') {
            steps {
                echo '🔍 Menjalankan linter...'
                sh 'npm run lint || true'  // Bisa di-skip kalau tidak ada skrip lint
            }
        }

        stage('Run Unit Test') {
            steps {
                echo '🧪 Menjalankan unit test...'
                sh 'npm test'
            }
            post {
                success {
                    echo '✅ Test berhasil'
                }
                failure {
                    echo '❌ Test gagal'
                }
            }
        }

        stage('Build (Opsional)') {
            steps {
                echo '⚙️ Build aplikasi...'
                sh 'npm run build || echo "Tidak ada perintah build"'
            }
        }

        stage('Deploy (Simulasi)') {
            steps {
                echo '🚀 Menjalankan aplikasi Node.js...'
                sh 'nohup node app.js &'
            }
        }
    }

    post {
        always {
            echo '🏁 Pipeline selesai.'
        }
    }
}
