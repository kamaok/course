node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/kamaok/course.git';
      // Get the Maven tool.
      // ** NOTE: This 'maven-demo' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'maven-demo'
   }
   stage('Deploy') {
      // Run the maven deploy
               sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean deploy"
         }
    stage('SonarQube analysis') {
    withSonarQubeEnv('my-sonarqube-demo') {
      // requires SonarQube Scanner for Maven 3.2+
      //sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
      sh "'${mvnHome}/bin/mvn' sonar:sonar"
      //sh "'${mvnHome}/bin/mvn' sonar:sonar -Dsonar.login=ae3f07fd81cfe5baeef37df9e293e7e316c3022a"
    }
   }
  }
