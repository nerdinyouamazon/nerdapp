pipeline{
  agent any
  environment {
    git_url='https://github.com/nerdinyouamazon/nerdapp'
    git_branch='main'  
      }
    stages {
      stage ("checkout"){
       steps {
          git branch:"${git_branch}",
          url: "${git_url}"
          
       }
      }
      stage ("dockerLogin"){
        steps{
             withcredentials{[
                usernamePassword(
                  credenyailsId: DHUB
                  userameVariable: 'D_user'
                  passwordVariable: 'D_pass'
                )

               
             ]}
         echo " usernmame - ${D_user}"
          
             
        }
      }
    }
  }
  

