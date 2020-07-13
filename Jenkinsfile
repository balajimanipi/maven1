node('master')
{
    stage('Continues Download') 
    {
     git 'https://github.com/balajimanipi/maven.git'
    }
    
    stage('Continues Build') 
    {
     sh label: '', script: 'mvn package'
    }
    
     stage('Continues Deployment') 
    {
     sh label: '', script: 'scp /var/lib/jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war root@172.31.38.180:/var/lib/tomcat8/webapps/testenv.war'
    }
     
    
    stage('Continues Testing') 
    {
     git 'https://github.com/balajimanipi/FunctionlTesting.git'
     sh label: '', script: 'java -jar /var/lib/jenkins/workspace/Scripted_Pipeline/testing.jar'
    }
    
    stage('Continues Delivery') 
    {
     input message: 'Waiting for Approval from the DM', submitter: 'ram' 
     sh label: '', script: 'scp /var/lib/jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war root@172.31.46.74:/var/lib/tomcat8/webapps/prodenv.war'
     
    }
    
}