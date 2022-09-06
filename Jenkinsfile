pipeline{
  agent any
  stages{
    stage('git-clone'){
     steps{
      checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'githubid', url: 'https://github.com/victoriababy45/team-parallel.git']]])
     } 
    }
    stage('actions1 and actions2'){
      parallel{
        stage('actions1'){
          steps{
            echo "actions1"
          }
        }
        stage('actions2'){
          steps{
            echo "actions2"
          }
        }
      }
    }
    stage('version-check'){
    	steps{
    		echo "end of parallel job"
    	}
    }
    stage('user-check'){
      steps{
        sh 'cat /etc/passwd | grep jenkins'
      }
    }
    stage('webhook-fix'){
      steps{
        echo "webhook fix"
      }
    }
  }
}
