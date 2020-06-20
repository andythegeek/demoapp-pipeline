pipeline {
  agent {
    node {
      label 'ubuntu-slave'
    }

  }
  stages {
    stage('Build') {
      steps {
        echo 'Building'
        sh 'sh run_build_script.sh'
      }
    }

    stage('LinuxTest') {
      parallel {
        stage('LinuxTest') {
          steps {
            echo 'Testing Linux'
            sh 'sh run_linux_tests.sh'
          }
        }

        stage('WindowsTest') {
          steps {
            echo 'Testing Windows'
          }
        }

      }
    }

    stage('Deploy to Production') {
      steps {
        input 'Deploy to production?'
      }
    }

  }
}