pipeline {
    agent any
    stages {
        stage('Production Deploy') {
            when {
                expression {
                    return env.GIT_TAG != null
                }
            }
            steps {
                echo "This is MAIN with TAG: ${env.GIT_TAG}"
            }
        }
    }
}
