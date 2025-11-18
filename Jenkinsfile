pipeline {
    agent any

    environment {
        APP_NAME = "SimpleApp"
        // Use env.BUILD_NUMBER to get the Jenkins build number
        VERSION = "1.0.${env.BUILD_NUMBER}"
    }

    stages {
        stage('Initialize') {
            steps {
                echo "Starting the pipeline for ${APP_NAME} version ${VERSION}"
                sh 'echo "Preparing workspace..."'
            }
        }

        stage('Build') {
            steps {
                echo "Building the application..."
                // Using triple double-quotes (""") allows multi-line scripts 
                // AND variable interpolation (replacing ${APP_NAME} with the value)
                sh """
                    mkdir -p build
                    echo "Application: ${APP_NAME}" > build/info.txt
                    echo "Version: ${VERSION}" >> build/info.txt
                    echo "Build completed successfully." >> build/info.txt
                """
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // Simple test: check that the build output file exists
                sh '''
                    if [ -f build/info.txt ]; then
                        echo "Test passed: build file exists."
                    else
                        echo "Test failed: build file missing!" && exit 1
                    fi
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${VERSION}..."
                sh """
                    mkdir -p deploy
                    cp build/info.txt deploy/
                    echo "Deployment complete." >> deploy/info.txt
                """
            }
        }

        stage('Archive Results') {
            steps {
                echo "Archiving build artifacts..."
                // Archives all .txt files found in the workspace
                archiveArtifacts artifacts: '**/*.txt', fingerprint: true
            }
        }
    }

    post {
        always {
            echo "Pipeline finished. Cleaning workspace..."
            // Removes the workspace directory to save disk space
            deleteDir()
        }
        success {
            echo "Build succeeded."
        }
        failure {
            echo "Build failed. Check logs for details."
        }
    }
}
