 pipeline {
          agent any 
	  stages    {

	  stage('clean')
	            {
		     steps {
		           echo 'this is maven clean'
			   sh 'mvn clean'
			   }
	            }
	  stage('build')
	            {
		    steps {
		            echo 'this is maven build'
			    sh 'mvn compile'

			  }
	             }
         stage('package')
	            {
		     steps {
		            echo 'this is maven package'
			    sh 'mvn package'
			    }
	             }
         stage('install')
	            {
		     steps {
		             echo 'this is maven istall'
			     sh 'mvn install'

			    }
	             }
         
	  stage('Test') {steps {
                              echo ' this is maven test'
                                sh 'mvn test'
                         } }
                          
                          
                   }
      
           post {
	        always {
		   mail to: meenakshi.m8@gmail.com, subject: 'The Pipeline failed' 
		      }
		 failure {
		    echo ' failed'
		     }
		}     
       //stage('deploy artifacts')//
                       //{steps {

//		             echo 'this is to deploy artifacts'//
//			     sh 'mvn deploy'//
                        
		       // }}//
                  
                   
     }       
