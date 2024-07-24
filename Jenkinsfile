pipeline {
    agent any
    stages {
        stage('Deploy to Dev') {
            steps {
                echo "Deploying in Dev"
                // Add your actual deployment steps for Dev here
            }
        }
        stage('Deploy to Prod') {
            options {
                timeout(time: 60, unit: 'SECONDS')
            }
            steps {
                script {
                    def userInput = input(
                        message: "Do you want to deploy in PROD?",
                        ok: "Approved",
                        submitter: "jenkins",
                        parameters: [
                            string(name: 'Change_Ticket', defaultValue: 'CHG123456', description: 'Please change ticket notes'),
                            string(name: 'USR_NAME', defaultValue: 'jenkins', description: 'Please provide your details'),
                            booleanParam(name: 'Approved_by_SRE', defaultValue: true, description: 'Is the build approved by SRE?'),
                            choice(name: 'CHOICES', choices: ['Release', 'HotFix', 'Rollback'], description: 'What is the kind of this build?'),
                            text(name: 'NOTES', defaultValue: 'Provide Description', description: 'Enter description'),
                            credentials(name: 'jenkinsCredes', description: "My credentials", required: true)
                        ]
                    )
                    
                    echo "Welcome ${userInput.USR_NAME}"
                    echo "Status of Approval is ${userInput.Approved_by_SRE}"
                    echo "This deployment is a ${userInput.CHOICES}"
                    echo "This deployment is done by ${env.USER}"
                    echo "Deploying in PROD"
                    // Add your actual deployment steps for Prod here
                }
            }
        }
    }
}
