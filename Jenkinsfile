pipeline{
  agent any
  stages{
    stage('Build'){
      steps{
        sh ' main/cloud.cpp -o output'
        build 'PES2UG20CS266-1'
        echo 'Build Successfully!'
      }
    }
    stage('Test'){
      steps{
        sh './output'
        echo 'Tested successfully!'
      }
    }
    stage('Deploy'){
      when{
        expression{
          currentBuild.result == null || currentBuild.result == 'SUCCESS'
        }
      }
      steps{
        echo 'Deployed Successfully!'
      }
    }
  }
  post{
    failure{
      echo 'Pipeline failed'
    }
  }
}
