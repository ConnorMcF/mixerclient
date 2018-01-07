node('node') {

    currentBuild.result = "PENDING"

    try {

       stage('Checkout') {

          checkout master
          
       }

       stage('Test') {

         env.NODE_ENV = "test"

         print "Environment will be : ${env.NODE_ENV}"

         sh 'node -v'
         sh 'npm prune'
         sh 'npm install'
         sh 'npm test'

       }

       stage('Cleanup') {

         echo 'prune and cleanup'
         sh 'npm prune'
         sh 'rm node_modules -rf'

       }

    }
    catch (err) {

        currentBuild.result = "FAILURE"
        throw err
        
    }

}
