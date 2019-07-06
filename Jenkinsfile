pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/apraka/jenkins_pipeline_hello'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'local maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'local maven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'local maven') {
                    sh 'mvn install'
                }
            }
        }

         
}
}
