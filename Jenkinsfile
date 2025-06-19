pipeline {
  agent any

  stages {
    stage('Get Git Tag') {
      steps {
        script {
          def isTag = env.GIT_BRANCH?.startsWith('refs/tags/')
          if (isTag) {
            echo "Triggered by tag: ${env.GIT_BRANCH}"
          } else {
            echo "Not a tag, skipping build"
            currentBuild.result = 'SUCCESS'
            return
          }
        }
      }
    }

    stage('Production Deploy') {
      when {
        expression { return env.GIT_BRANCH?.startsWith('refs/tags/') }
      }
      steps {
        echo 'Deploying to production...'
      }
    }
  }
}
