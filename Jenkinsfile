node {
    stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/staiyeba/gildedrose.git'
   }
   stage('Build') {
      // Run the maven build
        sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'

   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
    
   stage('Javadoc') {
        sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
        archive 'target/site/**/*'
        archive 'target/gildedrose-*.jar'
        //  archive 'target/site/**/*' // backs up the whole target site with the gildedrose jar as well
   }
}
