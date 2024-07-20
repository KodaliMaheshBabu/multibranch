pipeline {
    agent any
    
    options {
        retry(3)
    }
    
    parameters {
        string(name: 'name', defaultValue: 'Ass', description: 'This is the biggest Ass')
        choice(name: 'Environment',
               choices: ['Dev', 'Test', 'UAT', 'PAT', 'PROD'],
               description: "Which environment do you want to deploy to?"
        )
    }
    
    stages {
        stage('Input') {
            steps {
                timeout(time: 30, unit: 'SECONDS') {
                    input message: "Are you sure that you want to build the app?", ok: 'yes', submitter: 'jenkins'
                }
                echo "Input and timeout test"
                echo "Hello ${params.name}"
                echo "Deploying to ${params.Environment}"
            }
        }
    }
}
