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
      stage ("docker"){
        steps{
            docker build -t sample:$(BUILD_NUMBER)
             
        }
      }
    }
  }
  

