pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // ambil kode terbaru dari GitHub
                git branch: 'Lizuu', url: 'https://github.com/Lioosh12/WebGacha-Indiraise.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                // build image docker dari Dockerfile
                sh 'docker compose build'
            }
        }

        stage('Run Container') {
            steps {
                // stop container lama, jalankan yang baru
                sh '''
                docker compose down
                docker compose up -d
                '''
            }
        }
    }

    post {
        success {
            echo '🎉 Deployment sukses, web berjalan di Docker!'
        }
        failure {
            echo '❌ Gagal build, cek log di Jenkins.'
        }
    }
}