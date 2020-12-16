pipeline {
    agent {
        label 'master'
    }
    tools {
        maven 'M3'
        git 'git'
    }
    stages {
        stage ('CleanWorkspace'){
            steps {
                echo "CleaningWS"
            }
        }
        stage ('BuildandCompile'){
            steps {
                git 'https://github.com/swagger-api/swagger-petstore.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Testing') {
            parallel {
                stage('UnitTest'){
                    steps {
                        echo "Unit Test is completed"
                    }
                }
                stage('IntTest') {
                    steps {
                        echo "Int test is done"
                    }
                }
            }
        }
        stage('SonarSCan') {
            when {
                branch 'feature-*'
            }
            steps {
                echo "Sonar for feature branch"
            }    
        }
        stage('DeploytoDev') {
            when {
                branch 'develop'
            }
            steps {
                echo "Deploy to Dev"
            }    
        }
        stage('DeploytoProd') {
            when {
                branch 'master'
            }
            steps {
                echo "Deploy to Prod"
            }    
        }
    }
}
