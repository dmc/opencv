pipeline {
   
    agent {
        label "${params.NODE_LABEL}"
    }
   stages {
      stage('clean') {
         steps {
             echo "clean"
             deleteDir()
         }
      }
      

      stage('cppcheck') {
         steps {
            echo "cppcheck"
            bat script: '"C:\\Program Files\\Cppcheck\\cppcheck.exe" --xml --xml-version=2 "modules\\core\\src" 2> cppcheck.xml'
         }
      }
   }
   post {
       success {
           echo "scuccess"
           recordIssues(tools: [cppCheck(pattern: 'cppcheck.xml')])
       }
    }
}
