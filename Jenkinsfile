pipeline {
  agent any
  stages {
    stage('init') {
      steps {
        sh 'echo "in init step"'
      }
    }
    stage('parallel1') {
      parallel {
        stage('parallel1') {
          steps {
            sh 'echo "in parallel-1 $(date)"'
          }
        }
        stage('error') {
          steps {
            sh 'echo "in parallel-2 $(date)"'
          }
        }
      }
    }
    stage('send status mail') {
      steps {
        sh '''(
  echo From: bhaskaro@gmail.com
  echo To: bhaskaro@gmail.com
  echo "Content-Type: text/html;"
  echo Subject: Test reulsts backup completed
  echo
  echo "Took backup of test restults, below are the list of files."
  #ls -lrth
  #cat backup_results.html
) | sendmail -t
'''
        }
      }
    }
  }