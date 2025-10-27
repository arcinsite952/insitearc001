pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo Building...'
            }
        }
        stage('Deploy') {
             {
                branch 'main'
            }
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
                                    execCommand: 'chmod -R 755 /home/u935056060/domains/steakin.insitearc.com/public_html'
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
