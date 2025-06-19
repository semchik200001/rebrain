pipeline {
    agent any

    environment {
        GIT_TAG = ''
    }

    stages {
        stage('Get Git Tag') {
            steps {
                script {
                    GIT_TAG = sh(
                        script: "git describe --tags --exact-match || echo ''",
                        returnStdout: true
                    ).trim()
                    echo "GIT_TAG: ${GIT_TAG}"
                }
            }
        }

        stage('Production Deploy') {
            when {
                expression {
                    return GIT_TAG != ''
                }
            }
            steps {
                echo "DEPLOYING tag: ${GIT_TAG} to production"
            }
        }

        stage('Skip Info') {
            when {
                expression {
                    return GIT_TAG == ''
                }
            }
            steps {
                echo "⚠️ Сборка без тега — деплой не выполняется"
            }
        }
    }
}
