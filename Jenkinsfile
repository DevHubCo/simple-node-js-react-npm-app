pipeline {
  agent {
    kubernetes {
      yaml '''
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: maven
    image: maven:alpine
    command:
    - cat
    tty: true
  - name: busybox
    image: busybox
    command:
    - cat
    tty: true
'''
    }

  }
  stages {
    stage('Run maven') {
      steps {
        container(name: 'maven') {
          sh 'ls'
        }

        container(name: 'busybox') {
          sh 'ls'
        }

      }
    }

    stage('yo') {
      steps {
        podTemplate()
        input 'Yo Yo'
      }
    }

  }
}