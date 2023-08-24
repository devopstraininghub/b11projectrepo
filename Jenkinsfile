pipeline {
    agent any

    stages {
        stage('CLONE SCM FROM GITHUB') {
            steps {
                echo 'Cloning facebook code '
				git 'https://github.com/wakaleo/game-of-life.git'

            }
        }
		
        stage('BUILD ARTIFACT') {
            steps {
                echo 'building code using maven '
			    sh 'mvn clean install '
            }
        }	
		
        stage('DEPLOY TO TOMCAT ') {
            steps {
                echo 'deploying to tomcat'
				deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://3.86.190.214:8081/')], contextPath: 'facebook', war: '**/*.war'
            }
        }		
    }
}
