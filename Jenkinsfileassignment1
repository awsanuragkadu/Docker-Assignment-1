pipeline {
    agent any

    stages {

        stage('Deploy 2026Q1 to C1 - Port 80') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/2026Q1']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git',
                        credentialsId: 'git-token'
                    ]]
                ])
                sh '''
                    mkdir -p /opt/deploy/C1
                    cp index.html /opt/deploy/C1/index.html
                    chmod 644 /opt/deploy/C1/index.html
                    docker stop C1 || true
                    docker rm C1   || true
                    docker run -d \
                        --name C1 \
                        -p 80:80 \
                        -v /opt/deploy/C1/index.html:/usr/local/apache2/htdocs/index.html \
                        httpd
                '''
            }
        }

        stage('Deploy 2026Q2 to C2 - Port 85') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/2026Q2']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git',
                        credentialsId: 'git-token'
                    ]]
                ])
                sh '''
                    mkdir -p /opt/deploy/C2
                    cp index.html /opt/deploy/C2/index.html
                    chmod 644 /opt/deploy/C2/index.html
                    docker stop C2 || true
                    docker rm C2   || true
                    docker run -d \
                        --name C2 \
                        -p 85:80 \
                        -v /opt/deploy/C2/index.html:/usr/local/apache2/htdocs/index.html \
                        httpd
                '''
            }
        }

        stage('Deploy 2026Q3 to C3 - Port 90') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/2026Q3']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/awsanuragkadu/Docker-Assignment-1.git',
                        credentialsId: 'git-token'
                    ]]
                ])
                sh '''
                    mkdir -p /opt/deploy/C3
                    cp index.html /opt/deploy/C3/index.html
                    chmod 644 /opt/deploy/C3/index.html
                    docker stop C3 || true
                    docker rm C3   || true
                    docker run -d \
                        --name C3 \
                        -p 90:80 \
                        -v /opt/deploy/C3/index.html:/usr/local/apache2/htdocs/index.html \
                        httpd
                '''
            }
        }
    }

    post {
        success {
            echo 'All 3 Apache containers deployed successfully!'
        }
        failure {
            echo 'Build failed. Check the stage logs above.'
        }
    }
}
