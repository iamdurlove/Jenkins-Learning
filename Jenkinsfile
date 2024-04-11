pipeline {
    agent any
    environment{
        name = 'durlav'
    }
    parameters{
        string(name: 'person', defaultValue: 'Durlav', description: "Who are you?")
        booleanParam(name: 'isMale', defaultValue: true, description: "Are you male?")
        choice(name: 'City', choices: ['Kathmandu', 'Pokhara', 'Butwal'], description: "Where do you live?")
        
    }
    stages {
        stage('Running a command') {
            steps {
             sh '''
             date
             '''
            }
        }
         stage('Environment Variables') {
             environment{
                 username = 'kali'
             }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${username}"'
                
            }
        }
         stage('Printing own variable') {
            steps {
                sh 'echo "${name}"'
            }
        }
        stage('Continue') {
            input{
                message "Should we continue"
                ok "Yes we should"
            }
            steps {
                sh 'echo "${name}"'
            }
        }
         stage('Parameters') {
            steps {
                sh 'echo "${person}"'
                sh 'echo "${isMale}"'
                sh 'echo "${City}"'
            }
        }
    }
     post{
            always{
                echo 'I will always say hello'
            }
            failure{
                echo 'Hello Failure'
            }
            success{
                echo 'Hello Success'
            }
        }
}
