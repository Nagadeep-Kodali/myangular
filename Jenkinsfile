pipeline {
agent {
label 'Ansible'
}

stages {

stage ('Checkout') 
{
steps
    {
    
        checkout scm
        
    }
    
}
stage ('Build1') 
{
    steps
    {
       sh "cd /home/naga ; sudo apt-get update "
       sh "cd /home/naga/node/Angular-JumpStart ; sudo curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash - "
       sh "cd /home/naga/node/Angular-JumpStart ; sudo apt-get install nodejs "
       sh "cd /home/naga/node/Angular-JumpStart ; sudo npm install -g @angular/cli@11.0.5 -y "
       sh "cd /home/naga/node/Angular-JumpStart ; sudo ng config -g cli.warnings.versionMismatch false "
       sh "cd /home/naga/node/Angular-JumpStart ; sudo ng build  "
       sh "cd /home/naga/node/Angular-JumpStart/ ; sudo npm start "
    }
}
stage ('copymodule')
    { 
        steps 
            {
           sh " sudo ansible-playbook /home/naga/copy.yml"
            }
}
}
}
