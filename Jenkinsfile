pipeline{
  agent any
  environment{
      NEW_VERSION='1.3.0'
  }
  tools{
        maven 'M3' 
  }
  parameters{
        //string(name:'VERSION', defaultValue:'', description: 'version to deploy prod')
        choice(name:'VERSION', choices:['1.1.0','1.2.0','1.3.0'], description:'')
        booleanParam(name:'executeTest', defaultValue:true, description:'')
  }
  stages{
    stage("build"){
      steps{
         echo 'building applications...'
         echo "building version ${NEW_VERSION}"
         echo "building vesrion by parameters ${params.VERSION}"
         sh "mvn install"
      }
    }
    stage("test"){
      when{
        expression{
             params.executeTest
           }
      }
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
