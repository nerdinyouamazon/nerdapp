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
      stage ("dockerLogn"){
        steps{
             withCredentials([
                usernamePassword(
                  credentialsId: 'DHUB',
                  usernameVariable: 'D_user',
                  passwordVariable: 'D_pass'
                )

               
             ]){
               sh 'echo $D_pass|docker login -u $D_user --password-stdin'
               sh ' docker push nerdinyou/sample:${BUILD_NUMBER} .
             }
             
        }
      }
    }
  }
  

