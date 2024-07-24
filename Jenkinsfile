pipeline {
    agent any
    stages{
        stage('Deploy to Dev') {
            steps{
                echo "Deploying in Dev"
            }
        }
        stage('Deploy to Prod') {
            options{
                timeout(time: 60, unit:'SECOUNDS')
            }
            input{
                message: "Do you want to deploy in PROD"
                ok "Approved"
                submitter: "jenkins"
                submitterParameter: "Who Approved"
                Parameter{
                    string{
                        name: 'Change_Ticket',
                        defaultValue: 'CHG123456',
                        description: 'Please Change ticket notes'
                    }
                    string{
                        name: 'USR_NAME',
                        defaultValue: 'jenkins',
                        description: 'Please Provide your details'
                    }
                    booleanParam(
                        name: 'Approved_by_SRE', 
                        defaultValue: true, 
                        description: 'Is the build approved by SRE'
                        )
                    choice(
                        name: 'CHOICES', 
                        choices: ['Release', 'HotFix', 'Roleback'], 
                        description: 'What is the kind of theis Build'
                        )
                    text(
                        name: 'NOTES', 
                        defaultValue: 'Provide Description', 
                        description: 'Do enter Description'
                        )
                    credentials{
                        name: 'jenkinsCredes',
                        description: "MyCreds",
                        required: true
                    }
                    }


                }
                steps{
                    echo "Welcome ${USR_NAME}"
                    echo "Status of Approval is ${Approved_by_SRE}"
                    echo "thsi deployment is a ${CHOICES}"
                    echo "This Deployment is done by ${Who Approved}"
                    echo "Deploying in PROD"
                    echo
                }
            }
        
        }
    }
}
