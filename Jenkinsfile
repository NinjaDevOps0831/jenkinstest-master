pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout'
            }
        }
        stage('Build') {
            steps {
                echo 'Clean Build'
                bat 'mvn clean compile'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing'
                bat 'mvn test'
            }
        }
        stage('JaCoCo') {
            steps {
                echo 'Code Coverage'
                jacoco()
            }
        }
        stage('Package')
	    {
	    	steps{
	    	  echo 'Package'
	    	  bat 'mvn package -DskipTests'    
	    	      
	    	  
	    	}
	    }
	    stage('Deploy')
	    {
	    	steps{
	    	  echo '## TO DO DEPLOYMENT ##'
	    	}
	    }
	   
	    stage('JUnit')
	     {
		     steps{
			       junit '/target/surefire-reports/*.xml'
		     }
	    }
	  
	    
	    
	    
	    
    }
    
    post {
        always {
	
	    	echo 'Qwikeye publisher'
	    	 qwikeye 'Team U'
	    	
        }
        success {
            echo 'JENKINS PIPELINE SUCCESSFUL'
        }
        failure {
            echo 'JENKINS PIPELINE FAILED'
        }
        unstable {
            echo 'JENKINS PIPELINE WAS MARKED AS UNSTABLE'
        }
        changed {
            echo 'JENKINS PIPELINE STATUS HAS CHANGED SINCE LAST EXECUTION'
        }
    }
}
