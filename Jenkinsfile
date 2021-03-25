pipeline{
  agent any
  environment{
      NEW_VERSION='1.3.0'
  }
  stages{
    stage("build"){
      steps{
         echo 'building applications...'
         echo "building version ${NEW_VERSION}"
      }
    }
    stage("test"){
      steps{
         echo 'testing applications...'
      }
    }
    stage("deploy"){
      steps{
         echo 'deploying applications...'
      }
    }
  }
}
