node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/codecentric/TDDTrainingApplication.git'
      // Get the Maven tool.
      // ** NOTE: This 'Maven 3.3.9' Maven tool must be configured
      // **       in the global configuration.
      mvnHome = tool 'Maven 3.3.9'

     env.JAVA_HOME="${tool 'Java 8 Open JDK'}"
     env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
     sh 'java -version'
   }
   stage('Build') {
      // Move into directory
      dir('TDDTrainingApplicationCC') {
      // Run the maven build
        sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
