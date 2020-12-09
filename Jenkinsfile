pipeline {
    agent {
        label 'node1'
    }
    tools {
        maven 'M3'
        git 'git'
    }
    stages {
        stage ('CleanWorkspace'){
            step {
                echo "CleaningWS"
            }
        }
        stage ('BuildandCompile'){
            steps {
                git 'https://github.com/swagger-api/swagger-petstore.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
    }
}
