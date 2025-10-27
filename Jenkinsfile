pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo Build successful!'
            }
        }

        stage('Deploy to Hostinger') {
            steps {
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'hostinger',
                            transfers: [
                                sshTransfer(
                                    sourceFiles: '**/*',
                                    removePrefix: '',
                                    remoteDirectory: '/home/u935056060/domains/steakin.insitearc.com/public_html',
                                    
                                )
                            ],
                            verbose: true
                        )
                    ]
                )
            }
        }
    }
}
