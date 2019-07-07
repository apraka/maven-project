pipeline {
    agent any


    stages 
    {
        
        stage ('SCM Checkout') {
          git 'https://github.com/prakashk0301/maven-project'
         }
    
    
    
        stage ('Compile Stage') 
        { agent: label 'maven'}
        {

            steps {
                withMaven(maven : 'LocalMaven') 
                {   
                    sh 'mvn compile' 
                }
                }
                  }
                                
            
        
        
        stage ('Testing Stage') {


            steps {
                withMaven(maven : 'LocalMaven')
                {
                    sh 'mvn test'
                }
                  }
                                 
        }

        
        stage ('install Stage') {
            steps {
                withMaven(maven : 'LocalMaven')
                {
                    sh 'mvn install'
                }
                                  
                   }
        }

    }      
}
