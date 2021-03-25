pipeline{
  agent any
  environment{
      NEW_VERSION='1.3.0'
  }
  tools{
        maven 'M3' 
  }
  stages{
    stage("build"){
      steps{
         echo 'building applications...'
         echo "building version ${NEW_VERSION}"
         sh "mvn install"
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
