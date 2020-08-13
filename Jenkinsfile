pipeline {
    agent any

    stages {
        stage('Git-Checkout') {
            steps {
                echo 'Git Stage'
                git credentialsId: 'b386beff-da45-4d1a-a617-3177c5ee7acc', url: 'https://github.com/marcelbanic/Jenkins-Pipeline-Repo.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Build Stage'
                sh label: '', script: 'bash /var/lib/jenkins/workspace/Jenkins_From_Github_Pipeline/Build.sh'
            }
        }
        stage('Unit-Test') {
            steps {
                echo 'Unit Testing'
                sh label: '', script: 'bash /var/lib/jenkins/workspace/Jenkins_From_Github_Pipeline/Unit.sh'
            }
        }
        stage('QC') {
            steps {
                echo 'QC Stage'
                sh label: '', script: 'bash /var/lib/jenkins/workspace/Jenkins_From_Github_Pipeline/Quality.sh'
            }
        }
        stage('Deploy') {
            steps {
			echo 'Deploy stage'
                sh label: '', script: 'bash /var/lib/jenkins/workspace/Jenkins_From_Github_Pipeline/Deploy.sh'
            }
        }
    }
    post {
    always {
      echo 'always runs regardless of Pipeline run status'
    }
    success {
      echo 'step will run only if the build is successful'
    }
    failure {
      echo 'Pipeline is currently in a "failed" state run, usually expressed in the Web UI with the red indicator.'
    }
    unstable {
      echo 'Pipeline has "unstable" state, usually by a failed test, code violations and other causes, in order to run. Usually represented in a web UI with a yellow indication.'
    }
    changed {
      echo 'Pipeline is running at a different state than the previously completed Pipeline'
    }
  }
}
