pipeline {
    agent any

    stages {
        stage('GIT CLONE ') {
            steps {
                echo 'GIT CLONE'
				git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
		
        stage('BUILD ARTIFACT') {
            steps {
                echo 'BUILD ARTIFACT'
				sh 'mvn clean install'
            }
        }

        stage('DEPLOY TOMCAT') {
            steps {
                echo 'DEPLOY TOMCAT'
				deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.211.69.196:8090/')], contextPath: 'facebook', war: '**/*.war'
				
            }
        }

		
    }
}
