pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time:30, unit: 'MINUTES')
        disableConcurrentBuild()
        retry(1)
    }
    environment {
        DEBUG = 'true'
    }
    parameters {
        string(name:'PERSON', defaultValue: 'Mr jenkins', description: 'who should i say hello')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: 'true', description: 'Toggle this value')
        choice(name: 'CHOICE', choices:['One','Two','Three'], description: 'Pick something')
        password(name:'PASSWORD', defaultValue: 'SECRET', description: 'Enter a Password')
    }
    stages {
        stage ('Build') {
            steps {
                sh 'echo This is Build stage'
                sh 'sleep 10'
            }
        }
        stage ('Test') {
            steps {
                sh 'echo This is Test stage'
                sh 'env'
            }
        }
        stage ('Deploy') {
            when {
                expression {env.GIT_BRANCH = "origin/main"}
            }
            steps {
                sh 'echo This is Deploy'
            }
        }
        stage ('print params') {
            steps {
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"
            }
        }
    }
}