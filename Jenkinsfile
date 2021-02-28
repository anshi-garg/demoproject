pipeline {
    agent any
    parameters{
        choice(name: 'VERSION_NUMBER',choices:['1.1','1.2','2.0','2.2'],description:'version')
        booleanParam(name: 'executedTests', defaultValue: true , description: 'executedTests')
    }
    
    stages {
       
        stage("build") {
             
            steps {
                
               script{

                   gv.buildApp()
               }
           }
        }
        stage("test") {
          when{
               expression {
                env.BRANCH_NAME =='s.hareere500-dev-patch-50009'  && params.executedTests
               }
            }
            steps {
                
                 script{

                   gv.testApp()
               }
            }
        }
        stage("deploy") {
             
            
            steps {
                
                script{

                   gv.deployApp()
               }
            }
        }
    }
    post {
        always{
            echo ' the building is done'

        }
        success{
            echo 'success'

        }
        failure{
            echo 'failure'

        }
        
    }
}
