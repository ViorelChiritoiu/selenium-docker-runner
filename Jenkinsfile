pipeline{

    agent any

    stages {

        stage('Start Grid') {
            steps {
                bat "docker-compose -f grid.yaml up -d"
            }
        }

        stage('Run Tests') {
            steps {
                bat "docker-compose -f test-suites.yaml up"
            }
        }
    }

    post {
        always {
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
            archiveArtifacts artifacts: 'C:\selenium_framework\selenium-docker\output\flight-reservation\emailable-report.html', followSymlinks: false
            archiveArtifacts artifacts: 'C:\selenium_framework\selenium-docker\output\flight-reservation\emailable-report.html', followSymlinks: false
        }
    }

}