pipeline {
    agent none  // Master does NOT run anything itself

    stages {
        stage('Deploy to Both Slaves in Parallel') {
            parallel {

                // ───── SLAVE-S1 (Zone A) ─────
                stage('Zone A — slave-s1') {
                    agent { label 'slave-s1' }  // runs only on slave-s1
                    stages {

                        stage('S1 — Deploy 2026Q1 to C1 Port 85') {
                            steps {
                                checkout([$class: 'GitSCM',
                                    branches: [[name: '*/2026Q1']],
                                    userRemoteConfigs: [[
                                        url: 'https://github.com/YOUR_USER/YOUR_REPO.git',
                                        credentialsId: 'git-token'
                                    ]]
                                ])
                                sh '''
                                    mkdir -p /opt/deploy/C1
                                    cp index.html /opt/deploy/C1/index.html
                                    chmod 644 /opt/deploy/C1/index.html
                                    docker stop C1 || true
                                    docker rm   C1 || true
                                    docker run -d --name C1 -p 85:80 \
                                        -v /opt/deploy/C1/index.html:/usr/local/apache2/htdocs/index.html \
                                        httpd
                                '''
                            }
                        }

                        stage('S1 — Deploy 2026Q2 to C2 Port 90') {
                            steps {
                                checkout([$class: 'GitSCM',
                                    branches: [[name: '*/2026Q2']],
                                    userRemoteConfigs: [[
                                        url: 'https://github.com/YOUR_USER/YOUR_REPO.git',
                                        credentialsId: 'git-token'
                                    ]]
                                ])
                                sh '''
                                    mkdir -p /opt/deploy/C2
                                    cp index.html /opt/deploy/C2/index.html
                                    chmod 644 /opt/deploy/C2/index.html
                                    docker stop C2 || true
                                    docker rm   C2 || true
                                    docker run -d --name C2 -p 90:80 \
                                        -v /opt/deploy/C2/index.html:/usr/local/apache2/htdocs/index.html \
                                        httpd
                                '''
                            }
                        }

                        stage('S1 — Deploy 2026Q3 to C3 Port 95') {
                            steps {
                                checkout([$class: 'GitSCM',
                                    branches: [[name: '*/2026Q3']],
                                    userRemoteConfigs: [[
                                        url: 'https://github.com/YOUR_USER/YOUR_REPO.git',
                                        credentialsId: 'git-token'
                                    ]]
                                ])
                                sh '''
                                    mkdir -p /opt/deploy/C3
                                    cp index.html /opt/deploy/C3/index.html
                                    chmod 644 /opt/deploy/C3/index.html
                                    docker stop C3 || true
                                    docker rm   C3 || true
                                    docker run -d --name C3 -p 95:80 \
                                        -v /opt/deploy/C3/index.html:/usr/local/apache2/htdocs/index.html \
                                        httpd
                                '''
                            }
                        }
                    }
                }

                // ───── SLAVE-S2 (Zone B) ─────
                stage('Zone B — slave-s2') {
                    agent { label 'slave-s2' }  // runs only on slave-s2
                    stages {

                        stage('S2 — Deploy 2026Q1 to C1 Port 85') {
                            steps {
                                checkout([$class: 'GitSCM',
                                    branches: [[name: '*/2026Q1']],
                                    userRemoteConfigs: [[
                                        url: 'https://github.com/YOUR_USER/YOUR_REPO.git',
                                        credentialsId: 'git-token'
                                    ]]
                                ])
                                sh '''
                                    mkdir -p /opt/deploy/C1
                                    cp index.html /opt/deploy/C1/index.html
                                    chmod 644 /opt/deploy/C1/index.html
                                    docker stop C1 || true
                                    docker rm   C1 || true
                                    docker run -d --name C1 -p 85:80 \
                                        -v /opt/deploy/C1/index.html:/usr/local/apache2/htdocs/index.html \
                                        httpd
                                '''
                            }
                        }

                        stage('S2 — Deploy 2026Q2 to C2 Port 90') {
                            steps {
                                checkout([$class: 'GitSCM',
                                    branches: [[name: '*/2026Q2']],
                                    userRemoteConfigs: [[
                                        url: 'https://github.com/YOUR_USER/YOUR_REPO.git',
                                        credentialsId: 'git-token'
                                    ]]
                                ])
                                sh '''
                                    mkdir -p /opt/deploy/C2
                                    cp index.html /opt/deploy/C2/index.html
                                    chmod 644 /opt/deploy/C2/index.html
                                    docker stop C2 || true
                                    docker rm   C2 || true
                                    docker run -d --name C2 -p 90:80 \
                                        -v /opt/deploy/C2/index.html:/usr/local/apache2/htdocs/index.html \
                                        httpd
                                '''
                            }
                        }

                        stage('S2 — Deploy 2026Q3 to C3 Port 95') {
                            steps {
                                checkout([$class: 'GitSCM',
                                    branches: [[name: '*/2026Q3']],
                                    userRemoteConfigs: [[
                                        url: 'https://github.com/YOUR_USER/YOUR_REPO.git',
                                        credentialsId: 'git-token'
                                    ]]
                                ])
                                sh '''
                                    mkdir -p /opt/deploy/C3
                                    cp index.html /opt/deploy/C3/index.html
                                    chmod 644 /opt/deploy/C3/index.html
                                    docker stop C3 || true
                                    docker rm   C3 || true
                                    docker run -d --name C3 -p 95:80 \
                                        -v /opt/deploy/C3/index.html:/usr/local/apache2/htdocs/index.html \
                                        httpd
                                '''
                            }
                        }
                    }
                }

            }
        }
    }

    post {
        success { echo 'All containers deployed on both slaves!' }
        failure { echo 'Build failed. Check stage logs.' }
    }
}
