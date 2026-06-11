pipeline {
    agent any

    environment {
        // 본인의 Docker Hub ID로 변경하세요
        DOCKER_HUB_USERNAME = 'kimjunghun555'
        IMAGE_NAME = 'react-app'
    }

    stages {
        stage('Checkout') {
            steps {
                // GitHub 저장소에서 소스코드 가져오기
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // 프론트엔드 이미지 빌드
                    sh "docker build -t ${DOCKER_HUB_USERNAME}/${IMAGE_NAME}:latest ./frontend"
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // 기존 컨테이너 및 볼륨 정리 (에러 발생 시 무시하고 진행)
                    sh 'docker-compose down || true'

                    // 도커 컴포즈로 컨테이너 실행
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    post {
        always {
            // 빌드 후 사용하지 않는 이미지 정리 (선택사항)
            sh 'docker image prune -f'
        }
        success {
            echo '배포가 성공적으로 완료되었습니다!'
        }
        failure {
            echo '배포에 실패했습니다. 로그를 확인하세요.'
        }
    }
}