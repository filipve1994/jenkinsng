pipeline {
  agent any
  stages {
    stage('Source') {
      steps {
        git(url: 'https://github.com/filipve1994/jenkinsng', branch: 'pipe1')
        sh 'env'
        script {
          def commitid = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
          echo commitid
          sh "echo ${commitid} > ${env.WORKSPACE}/expectedCommitid.txt"
        }

        script {
          sh "echo ${env.PATH}"
          nodejs('node') {
            sh "npm -v"
          }

        }

      }
    }
    stage('copy to tmp folder') {
      steps {
        sh 'cp -R /dist/* /tmp/angularprojects/'
      }
    }
  }
  tools {
    nodejs 'NodeJS'
  }
}