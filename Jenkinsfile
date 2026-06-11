pipeline {
agent any

```
stages {

    stage('Checkout') {
        steps {
            checkout scm
        }
    }

    stage('Deploy') {
        steps {
            sh '''
                docker compose down || true
                docker compose build --no-cache
                docker compose up -d
            '''
        }
    }
}

post {
    success {
        echo '배포 완료'
    }

    failure {
        echo '배포 실패'
    }
}
```

}
