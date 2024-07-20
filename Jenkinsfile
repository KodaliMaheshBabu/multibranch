pipeline{
    agent any
    stages{
        stage('Input'){
            steps{
                timeout(time: 30, unit: 'SECONDS') {
                    input message: "Are you sure that you are building the app", ok:'yes', submitter: 'jenkins'
                }
                echo "input and timeout test"
            }
        }
    }
}
                
