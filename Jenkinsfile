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
              sh  """
                echo $D_pass|docker login -u $D_user --password-stdin
                 docker build -t sample:${BUILD_NUMBER} .
                 docker tag sample:${BUILD_NUMBER} nerdinyou/sample:${BUILD_NUMBER}
                 docker push nerdinyou/sample:${BUILD_NUMBER}
               """
             }
             
        }
      }
    }
  post {

    success {
        emailext(
            subject: "SUCCESS - ${JOB_NAME} #${BUILD_NUMBER}",
            body: "Image pushed successfully.",
            to: "nerdinyouamazon@gmail.com"
        )
    }

    failure {
        emailext(
            subject: "FAILED - ${JOB_NAME} #${BUILD_NUMBER}",
            body: "Pipeline failed. Check ${BUILD_URL}",
            to: "nerdinyouamazon@gmail.com"
        )
    }

    always {
        echo 'Pipeline completed'
    }
}
  }
  

