pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/apraka/maven-project'
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

        stage ('deploy stage'){
            steps {
                sshagent(credentials: ['c22fbfa0-ca3b-46e9-997a-e9c5b219d37b']) {
                    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.37.80:/var/lib/tomcat/webapps'
                }
            }
        } 
}
         
}
}
