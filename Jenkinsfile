pipeline {
    agent any 
    stages {
        stage ('Build') {
            steps {
                echo "Building node application"
            }
        }
        stage ('Deploy to prod') {
            options {
                timeout(time: 30, unit: 'SECONDS')
            }
            input {
                message "Should i continue ??"
                ok "Approved"
                submitter "maha"
                submitterParameter "whoapproved"
                parameters {
                    string (
                        name: 'USR_NAME',
                        defaultValue: 'Siva',
                        description: 'Do enter your name'
                    )
                    string (
                        name: 'CHG_Ticket',
                        defaultValue: 'CHG1234',
                        description: 'Do enter your name'
                    )
                    booleanParam(
                        name: 'SRE_APPROVED',
                        defaultValue: true,
                        description: 'Is SRE approval taken for this release'
                    )
                    choice(
                        choices: 'Regular\nHotfix',
                        description: "What sort of release is this, regulare release or hotfix ?",
                        name: 'Release'
                    )
                    text(
                        name: 'Notes',
                        defaultValue: "Enter Release notes",
                        description: "Do enter the description"
                    )
                    credentials(
                        name: 'mycrediantials',
                        description: "myCredentials", 
                        required: true
                    )
                }
            }
            steps {
                echo "Deploying to production"
                echo "Welcome ${USR_NAME}"
                echo "Status of approval ${SRE_APPROVED}"
                echo "This is a ${Release} Release"
                echo "Approved by this person: ${whoapproved}"
            }
        }
    }
            post{
            success{
                echo "Job is done"
            }
            always{
                echo "Job is done please check if failed or passed"

            }
            changed{
                echo "Job is changed"
            }
            fixed{
                echo "Job is fixed"

            }
            regression{
                echo "Job is regression"

            }
            aborted{
                echo "Job is aborted"

            }
            failure{
                echo "Job is failure"

            }
            unstable{
                echo "Job is unstable"

            }
            unsuccessful{
                echo "Job is unsuccessfull"

            }
            cleanup{
                echo "Job is cleanUp"

            }
        }
}
