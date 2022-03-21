node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       app = docker.build("anzurakizz/kiii-homework")
    }

//    stage('Test image') {
//  
//
//        app.inside {
//            sh 'rm /'
//        }
//    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}

// jenkins secret 111d54b55e08c618d3310fd752f8aedb6a
