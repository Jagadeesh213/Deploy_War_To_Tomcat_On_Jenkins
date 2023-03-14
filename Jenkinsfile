node{

   def tomcatWeb = 'D:\\Auto_deployment\\apache-tomcat-8.5.87\\apache-tomcat-8.5.87\\webapps'
   def tomcatBin = 'D:\\Auto_deployment\\apache-tomcat-8.5.87\\apache-tomcat-8.5.87\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/ Jagadeesh213/simple-java-maven-app.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\simple-java-maven-app.war \"${tomcatWeb}\\simple-java-maven-app.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
