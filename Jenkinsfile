pipeline {
    agent none

    stages {

        stage('Deploy on Both Slaves') {
            parallel {

                stage('Deploy on Slave1 (zoneA)') {
                    agent { label 'zoneA' }

                    stages {

                        stage('Q1 → C1') {
                            steps {
                                git branch: '2026Q1', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'
                                sh '''
                                docker cp index.html C1:/usr/local/apache2/htdocs/index.html
                                '''
                            }
                        }

                        stage('Q2 → C2') {
                            steps {
                                git branch: '2026Q2', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'
                                sh '''
                                docker cp index.html C2:/usr/local/apache2/htdocs/index.html
                                '''
                            }
                        }

                        stage('Q3 → C3') {
                            steps {
                                git branch: '2026Q3', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'
                                sh '''
                                docker cp index.html C3:/usr/local/apache2/htdocs/index.html
                                '''
                            }
                        }
                    }
                }

                stage('Deploy on Slave2 (zoneB)') {
                    agent { label 'zoneB' }

                    stages {

                        stage('Q1 → C1') {
                            steps {
                                git branch: '2026Q1', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'
                                sh '''
                                docker cp index.html C1:/usr/local/apache2/htdocs/index.html
                                '''
                            }
                        }

                        stage('Q2 → C2') {
                            steps {
                                git branch: '2026Q2', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'
                                sh '''
                                docker cp index.html C2:/usr/local/apache2/htdocs/index.html
                                '''
                            }
                        }

                        stage('Q3 → C3') {
                            steps {
                                git branch: '2026Q3', url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git'
                                sh '''
                                docker cp index.html C3:/usr/local/apache2/htdocs/index.html
                                '''
                            }
                        }
                    }
                }
            }
        }
    }
}
