pipeline {
    agent none
    stages {
	
	stage('Non-Parallel Stage') {
	    agent {
                        label "Master"
                }
        steps {
                echo 'This is First Stage'
                }
        }

	
        stage('Run Tests') {
            parallel {
                stage('Test Stage') {
                    agent {
                        label "Unix_System"
                    }
                    steps {
                        echo "Task1"
                    }
                    
                }
                stage('Test On Master') {
                    agent {
                        label "Master"
                    }
                    steps {
						echo "Task1 on Master Node"
					}
                }
            }
        }
    }
}
