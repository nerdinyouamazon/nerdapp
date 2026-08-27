pipeline{
  agent any
  environment {
    git_url='https://github.com/nerdinyouamazon/nerdapp'
    branch='main'  
      }
    stages {
      stage ("checkout"){
       steps {
        git branch :$(branch),
          url $(git_url)
          sh 'date'
       }
      }
    }
  }
  

