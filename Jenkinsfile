pipeline
{
    agent {label 'master'}
    stages('CICD')
    {
    stage('Continuous Download')
    {
        steps
        {
        script
        {
            try
            {
                git 'https://github.com/aditya1941/mavenproject.git'
            }
            catch(Exception e001)
            {
                mail bcc: '', body: 'Please check Jenkins continuous download failed', cc: 'dev1@gmail.com', from: '', replyTo: '', subject: 'Download Failed', to: 'dev@gmail.com'
                exit(1)
            }
        }
        }
    }
    stage('Continuous Build')
    {
        steps
        {
        script
        {
            try
            {
                sh 'mvn package'
            }
            catch(Exception e002)
            {
                mail bcc: '', body: 'Please check Jenkins continuous build failed', cc: 'mid1@gmail.com', from: '', replyTo: '', subject: 'build Failed', to: 'mid@gmail.com'
                exit(1)
            }
        }
        }
    }
    stage('Continuous Deploy')
    {
        steps
        {
        script
        {
            try
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/scripted/webapp/target/webapp.war ubuntu@172.31.33.207:/var/lib/tomcat9/webapps/qa.war'
            }
            catch(Exception e003)
            {
                mail bcc: '', body: 'Please check Jenkins continuous deploy failed', cc: 'test1@gmail.com', from: '', replyTo: '', subject: 'depl Failed', to: 'test@gmail.com'
                exit(1)
            }
        }
        }
    }
    stage('Ctest')
    {
        steps
        {
        script
        {
            try
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                 sh 'java -jar /home/ubuntu/.jenkins/workspace/newp/testing.jar'
            }
            catch(Exception e004)
            {
                mail bcc: '', body: 'Please check Jenkins continuous deploy failed', cc: 'test1@gmail.com', from: '', replyTo: '', subject: 'depl Failed', to: 'test@gmail.com'
                exit(1)
            }
        }
        }
    
    }
    stage('CDelivery')
    {
        steps
        {
        script
        {
            try
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/newp/webapp/target/webapp.war ubuntu@172.31.41.104:/var/lib/tomcat9/webapps/pr.war'
            }
            catch(Exception e005)
            {
                mail bcc: '', body: 'Please check Jenkins continuous deploy failed', cc: 'test1@gmail.com', from: '', replyTo: '', subject: 'depl Failed', to: 'test@gmail.com'
                exit(1)
            }
        }
        }
    }
    }
     post
     {
     success
     {
     echo 'success'
     }
     failure
     {
     echo 'failure'
     }
     always
     {
     echo 'executed'
     }
     abort
     {
     echo 'aborted'
     }
     change
     {
     echo 'changed'
     }
    }
}
}
