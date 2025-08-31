pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }

        stage("Deploy"){
            steps{
                sh '''
                   oc project shigve-deploy-strategies 
                   oc start-build greeting-strategy --follow --wait
                '''
            }
        }

        // Add the "Deploy" stage here
    }
}
