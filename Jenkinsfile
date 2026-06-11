services:

  json-server:
    build:
      context: ./frontend/server

    container_name: json-server

    ports:
      - "3001:3001"

    restart: unless-stopped

  nginx:
    build:
      context: .
      dockerfile: nginx/Dockerfile

    container_name: nginx

    depends_on:
      - json-server

    ports:
      - "80:80"

    restart: unless-stopped
    stage('Install Frontend') {
                steps {
                    dir('frontend') {
                        sh 'npm install'
                    }
                }
            }

            stage('Build Frontend') {
                steps {
                    dir('frontend') {
                        sh 'npm run build'
                    }
                }
            }

            stage('Deploy') {
                steps {
                    sh '''
                        docker-compose down || true
                        docker-compose build --no-cache
                        docker-compose up -d
                    '''
                }
            }

            stage('Check Containers') {
                steps {
                    sh '''
                        docker ps
                    '''
                }
            }
        }

        post {

            success {
                echo '========================'
                echo '배포 완료'
                echo '========================'

                sh '''
                    docker ps
                '''
            }

            failure {
                echo '========================'
                echo '배포 실패'
                echo '========================'

                sh '''
                    echo "===== Docker PS ====="
                    docker ps -a || true

                    echo "===== Docker Images ====="
                    docker images || true
                '''
            }

            always {
                sh 'docker ps || true'
            }
        }
    }