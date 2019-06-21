pipeline {
  agent {
    node {
      label 'master'
    }

  }
  
  tools {nodejs "NodeJS"}
  
  stages {
    stage('Source') {
      steps {
        tool 'NodeJS'
        git(url: 'https://github.com/filipve1994/jenkinsng', branch: 'pipe1')
        sh 'env'
        script {
          def commitid = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
          echo commitid
          sh "echo ${commitid} > ${env.WORKSPACE}/expectedCommitid.txt"
        }

      }
    }
    stage('Build') {
      steps {
        sh 'npm config ls'
        sh 'npm install'
        sh 'ng build'
      }
    }
    stage('copy to tmp folder') {
      steps {
        sh 'cp -R /dist/* /tmp/angularprojects/'
      }
    }
  }
}
