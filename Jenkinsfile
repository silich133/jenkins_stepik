pipeline {
    agent any
    stages {
        stage('Prepare') {
            steps {
                echo 'Preparing workspace...'
                sh 'mkdir -p build logs temp'
                echo 'Directories created'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'echo "Build version: 1.0.0" > build/version.txt'
                sh 'date >> build/version.txt'
                echo 'Build completed'
            }
        }

        stage('Verify') {
            steps {
                echo 'Verifying build...'
                sh 'cat build/version.txt'
                sh 'ls -la build/'
                echo 'Verification completed'
            }
        }

        stage('System Info') {
            steps {
                echo '=== System Information ==='
                echo 'Current user: '
                sh 'whoami'
                echo 'Disk info: '
                sh 'df -h .'
                echo "Build Number: ${BUILD_NUMBER}"
                echo '=== End Of System Information ==='
            }
        }

        stage('Cleanup') {
            steps {
                echo 'Cleaning up temporary files...'
                sh 'rm -rf temp logs'
                sh 'ls -la'
                echo 'Cleanup completed'
            }
        }
    }
}
