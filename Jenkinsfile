node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email vishnu2017it029@abesit.edu.in"
                        sh "git config user.name V1SHNU08"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+163048243785.dkr.ecr.me-central-1.amazonaws.com/watani-preprod.*+163048243785.dkr.ecr.me-central-1.amazonaws.com/watani-preprod:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git init"
                        sh "git add --all"
                        sh "git commit -m 'Done by Jenkins Job changemanifest"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
      }
    }
  }
}
}
