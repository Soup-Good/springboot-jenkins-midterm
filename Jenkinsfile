pipeline { 
	agent any 

	options { 
	    skipStagesAfterUnstable()
	}

	tools { 
	    maven '3.9.11'
	}
	
	stages { 
	    stage('Checkout Source Code') { 
		steps {
		   git branch: 'main', url: 'https://github.com/Soup-Good/springboot-jenkins-midterm.git'
		}
	    }
		
	    stage('Test') {
	        steps { 
		    sh 'git --version' 
		    sh 'mvn --version' 
		    sh 'mvn clean test' 
	        } 
	    }

	    stage ('Build and Package') { 
		steps { 
		    sh 'mvn clean apckage -DskipTests'
		} 
	    }

	    stage('Archive Artifacts') { 
	        steps { 
		    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
		}
	    } 
	}
	
	post { 
	    always { 
		echo 'Pipeline Finished'
	    }
	    success { 
		echo 'IT WORKS!' 
	    } 
	    failure { 
		echo 'Failed!' 
	    } 
	} 
}
