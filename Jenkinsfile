pipeline {
    agent none

    stages {

        stage('Deploy Q1') {
            agent { label 'zoneA' }   // runs on slave-s1

            steps {
                git branch: '2026Q1', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'

                sh '''
                docker cp index.html C1:/usr/local/apache2/htdocs/index.html
                '''
            }
        }

        stage('Deploy Q2') {
            agent { label 'zoneB' }   // runs on slave-s2

            steps {
                git branch: '2026Q2', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'
                sh '''
                docker cp index.html C2:/usr/local/apache2/htdocs/index.html
                '''
            }
        }

        stage('Deploy Q3') {
            agent { label 'zoneA' }   // you can choose any slave

            steps {
                git branch: '2026Q3', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'

                sh '''
                docker cp index.html C3:/usr/local/apache2/htdocs/index.html
                '''
            }
        }
    }
}
