pipeline {
    agent any
    stages {
        stage('Build NPM') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS_11_4_0') {
                    sh 'cd src/main/frontend && npm install && npm run build'
                }
            }
        }
        stage('Build Java') {
            steps {
                withMaven(maven : 'maven_3_6_0') {
                    sh 'mvn clean install'
                }
            }
        }
        stage('Create Docker Image') {
            steps {
                sh 'docker build -t thewaterwalker/spring-boot-ldap-react:latest .'
            }
        }
    }
}
