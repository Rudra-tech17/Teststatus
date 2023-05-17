pipeline {
  agent any
  stages {
    stage('skip ci') {
      when {
        branch 'develop'
      }
      steps {
        script {
           if (sh(script: "git log -1 --pretty=%B | fgrep -ie '[ci skip]'", returnStatus: true) == 0) {
              currentBuild.result = 'NOT_BUILT'
              error 'Aborting because commit message contains [ci skip]'
           }
        }
      }
    }
    stage('build womething') {
      when {
        branch 'develop'
      }
      steps { 
        sh 'echo "Build Something"'
      }
    }
  }
}
