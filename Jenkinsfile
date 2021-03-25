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
    stage("init){
          steps{
            script{
                gv=load "script.groovy"   
            }
         }
     }
    stage("build"){
      when{
        expression{
             params.executeTest
           }
      }
      steps{
         script{
                gv.buildApp() 
            }
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
          script{
                gv.testApp() 
            }
         echo 'testing applications...'
      }
    }
    stage("deploy"){
      steps{
          script{
                gv.deployApp() 
            }
         echo 'deploying applications...'
      }
    }
  }
}
