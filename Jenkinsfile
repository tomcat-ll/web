pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '2938767e-a4c5-43e7-928c-cee7103b3121', url: 'https://github.com/tomcat-ll/web.git']]])
            }
        }
        stage('build project ') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('publish project ') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '35b8c81c-81e3-415b-ada9-d786505bad4a', path: '', url: 'http://192.168.5.101:9090/')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}