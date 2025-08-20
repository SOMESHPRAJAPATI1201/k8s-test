pipeline{
    agent {
        kubernetes {
            label 'test-app'
            yaml """
apiVersion: v1
kind: Pod
metadata:
  name: mysql-pod
  labels:
    app: mysql
spec:
  serviceAccountName: default
  containers:
    - name: mysql
      image: mysql:8.0
      ports:
        - containerPort: 3306
      env:
        - name: MYSQL_ROOT_PASSWORD
          value: root
        - name: MYSQL_DATABASE
          value: mydb
      volumeMounts:
        - name: mysql-storage
          mountPath: /var/lib/mysql
    - name: docker
      image: docker:latest
      command: ["sh", "-c", "while true; do sleep 30; done;"]
  volumes:
    - name: mysql-storage
      emptyDir: {}
"""
    }
}
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build commands here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test commands here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deployment commands here
            }
        }
    }

    post {
        always {
            echo 'This will always run after the pipeline completes.'
        }
        success {
            echo 'This will run only if the pipeline succeeds.'
        }
        failure {
            echo 'This will run only if the pipeline fails.'
        }
    }
}