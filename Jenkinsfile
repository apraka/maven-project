pipeline {
    agent any

    stages {
        stage('SCM Checkout'){
		  steps{
		     git 'https://github.com/prakashk0301/maven-project.git'
			 }
        }
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Localmaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Localmaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'Localmaven') {
                    sh 'mvn install'
                }
            }
        }
	    stage ('build && SonarQube analysis') {
            steps {
		        withSonarQubeEnv('sonar') {
                    withMaven(maven : 'Localmaven') {
                        sh 'mvn clean package sonar:sonar'
                    }
		        }	
            }
        }
}
}
