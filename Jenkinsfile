pipeline {
    agent any
    parameters {
        choice(name: 'NUMBER',
            choices: [10,20,30,40,50,60,70,80,90],
            description: 'Select the value for F(n) for the Fibonacci sequence.')
    }
    options {
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
        timeout(time: 12, unit: 'HOURS')
        timestamps()
    }
    triggers {
        cron '@midnight'
    }
    stages {
        stage('Make executable') {
            steps {
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c "chmod +x $WORKSPACE/scripts/fibonacci.sh"'
            }
        }
        stage('Relative path') {
            steps {
                bat "C:\\Program Files\\Git\\bin\\bash.exe -c \"$WORKSPACE/scripts/fibonacci.sh ${params.NUMBER}\""
            }
        }
        stage('Full path') {
            steps {
                bat "C:\\Program Files\\Git\\bin\\bash.exe -c \"$WORKSPACE/scripts/fibonacci.sh ${params.NUMBER}\""
            }
        }
        stage('Change directory') {
            steps {
                bat "C:\\Program Files\\Git\\bin\\bash.exe -c \"cd $WORKSPACE/scripts && ./fibonacci.sh ${params.NUMBER}\""
            }
        }
    }
}
