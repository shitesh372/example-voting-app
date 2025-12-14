pipeline{ 
    agent {any} 
    options { 
      buildDiscarder(logRotator(numToKeepStr: '15'))
     disableConcurrentBuilds() 
     retry(2) 
     timeout(time: 20, unit: 'MINUTES')
      }
       parameters { 
        string(name: 'BRANCH', defaultValue: 'main', description: 'branch to build?')
        choice(name: 'ENV', choices: ['qa', 'dev', 'prod'], description: 'env to build')
         } 
         stages{ 
         stage("Docker login and push"){
         steps{ 
          sh "docker login -u shitesh3796 -p Kunal@0315." 
          sh ''' 
          cd vote 
          docker build -t shitesh3796/vote:v${BUILD_NUMBER} . 
         '''
          sh "docker push shitesh3796/vote:v${BUILD_NUMBER}" 
          }
          } 
          stage("deploy"){ 
            steps{ 
              sh "echo starting deployment" } 
          }
           }
            }
