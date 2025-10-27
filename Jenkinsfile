pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Running build steps...'
                // Example build command (modify if needed)
                sh 'echo "Build successful!"'
            }
        }

        stage('Deploy to Hostinger') {
            when {
                branch 'main'  // only deploy on main branch
            }
            steps {
                echo 'Deploying to Hostinger server via SSH...'
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'hostinger',   // name from Jenkins → Configure System → Publish over SSH
                            transfers: [
                                sshTransfer(
                                    sourceFiles: '**/*',  // upload all files (adjust if needed)
                                    removePrefix: '',     // optional
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
