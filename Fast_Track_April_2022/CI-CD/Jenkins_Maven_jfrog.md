# JENKINS and MAVEN

# Maven:
* Maven is a build automation tool and it helps DevOps in providing automation around the Build phase of the DevOps Life Cycle Management.

## Build tools
   * c => Make, GCC
   * Java => Ant, Maven, Gradle
   * .net => MSBuild, dotnet build

## Install maven 

```
sudo apt update
sudo apt install maven
mvn -version
```

## MAVEN GOALS:
  * compile
  * Test
  * package
  * Install
  * clean
## compile: __mvn compile__
* Compile : - compile the source code
* when you  do  ```__mvn compile__```. It creates the  classfile.

## Test:  __mvn test__
* test :- run unit tests

## package :  __mvn package__
* This will create the package (.war/.jar/.ear)

## clean :  __mvn clean__
* when you do clean , it will delete the old war and create the war.
* Basically the output will be stored in the target folder.

```
mvn test = mvn compile + mvn test
mvn package = mvn compile + mvn test + mvn package

```

## POM.XML : -  Developer defines the dependencies to build the project and also he will define the output of the build:
* POM stands for Project Object Model. It is the fundamental unit of work in the Maven. It is an XML file. It consists of all the information about the projects and the build configuration details used to build the project. It resides in the base directory of the Maven as the pom.xml
![preview](../images/jenkins40.png) 


## Types of Maven repositories : - central, local, and remote
![preview](../images/jenkins38.png)
![preview](../images/jenkins39.png)  

## Build the code manually using maven:
* Clone the code from github.
```
git clone https://github.com/devops-surya/game-of-life.git
cd game-of-life.git
```
![preview](../images/jen21.png)  
![preview](../images/jen22.png)  
* __mvn package__
![preview](../images/jen23.png)  
![preview](../images/jen24.png)  



# Jenkins:
* Jenkins is an open source continuous integration/continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.
* Jenkins is a ci/cd tool
* ci -- continous integration 
* cd -- continous delivery / continous deployment

## Basic flow of devops :
![preview](../images/jenkins1.png)
![preview](../images/jenkins2.png)
![preview](../images/jenkins3.png)


## Installing jenkins 
* prerequisites:
1. Ubuntu
2. Java 
3. Jenkins

## For installing jenkins we have two ways.
1. Jenkins master 
2. Quick setup (it is not the enterprize setup)
* For quick setup [REFER HERE](https://www.jenkins.io/download/)
```
 java-jar <path to the download>
```
## For installing jenkins master :
* For the jenkins installation [REFER HERE](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu) 


```
sudo apt-get update
sudo apt-get install openjdk-8-jdk

java -version

wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
```

* To open jenkins on brower 

```
http://ipaddress:8080
```
* After using above command we will get below screen on browser:
![preview](../images/jenkins4.png)
 * Copy the password and paste it on the browser:
![preview](../images/jenkins5.png)
* Click on the install suggested plugins , then u will see below page:
![preview](../images/jenkins6.png)
* provide the username, password , email:
![preview](../images/jenkins7.png)
* After providing usename and password click on the save and continue:
![preview](../images/jenkins8.png)
* Dashboard of jenkins
![preview](../images/jenkins9.png)

## Create a new job:
![preview](../images/jenkins10.png)

## Manage jenkins is used to configure the jenkins (settings) :
![preview](../images/jenkins11.png)

## Jenkins executor :
* Executor will define , how many jobs run parallely at a time.
![preview](../images/jenkins12.png)

## Multiple ways to create a job:
![preview](../images/jenkins13.png)

## Create a job in Freestyle:
* click on the newitem and follow the below screenshots :
![preview](../images/jenkins14.png)
![preview](../images/jenkins15.png)
![preview](../images/jenkins16.png)
![preview](../images/jenkins17.png)

## Jenkins workspace, Jobs, Builds, Jenkins HOME_PATH/HOME_DIRECTORY :
* All the jenkins stuff will be stored in the jenkins HOME_PATH = /var/lib/jenkins/
* /var/lib/jenkins/workspace : - Jenkins workspace for everyjob is stored
![preview](../images/jen16.png)
* /var/lib/jenkins/jobs : - Configurations of everyjob is stored
![preview](../images/jen15.png)
* Delete workspace before every build ,it removes the workspace for every build.
![preview](../images/jenkins46.png)


## Multiple sections in jenkins freestyle job:
1. General
2. Source Code Management
3. Build Triggers
4. Build Environment
5. Build 
6. Post-build Actions

![preview](../images/jen3.png)

## 1. General :
* Description : - Describe about your job
* Discard old builds : - No of days / No of build to be exists 
![preview](../images/jen4.png)
* This project is parameterized : - When can use parameters 
![preview](../images/jen5.png)
* Disable this project  : -  It will disable the project like can't Run/build the job
![preview](../images/jen6.png)
* Execute concurrent builds if necessary : - It allows you to run the same job multipletimes parallely
![preview](../images/jen7.png)


## 2. Source Code Management:
* Git : - Provide Githuburl/credentials , Branch to build 
![preview](../images/jen8.png)

## 3. Build Triggers:
* Trigger builds remotely : - Triggers the remote other jobs 
* Build after other projects are built : - Its allows you to build the present job after any succesfull job
![preview](../images/jen9.png)
* Build periodically : - It build the job at given schedule
![preview](../images/jen10.png)
* Poll SCM : - It build the job at given schedule , only when there are changes in code repository
![preview](../images/jen11.png)

## 4. Build Environment:
* Delete workspace before build starts : - Delete and creates a new workspace for every build
![preview](../images/jen12.png)

## 5. Build:
* Define all your build steps here :
![preview](../images/jen13.png)
* Invoke top-level Maven targets : - Invoke the maven steps here
![preview](../images/jenkins41.png) 
![preview](../images/jenkins42.png)  

## 6. Post-build Actions:
* Define all you Post-build action steps here 
![preview](../images/jen14.png)


## Archive the artifacts / Publish JUnit test results report :
### Create a job for GOL build.
1. Create a freestyle job with name __gol__
2. SCM -- provide the github url 
3. POLLSCM --- * * * * *
4. Delete the workspace for every build
5. BUILD -- Provide the goal in the invoke top-level maen plugin.

![preview](../images/jenkins47.png)

![preview](../images/jenkins48.png)

5. Build the job.

![preview](../images/jenkins49.png)

6. Go to configure and add post build actions as below:

![preview](../images/jen1.png)

7. Build the job and ouput will be as below:

![preview](../images/jenkins51.png)

* Artifacts are nothing but the war/jar/ear files.

8. Go to configure and add the publish junit test results as below:

![preview](../images/jen1.png)

9. Build the job and output will be as shown below:

![preview](../images/jenkins53.png)

## Build with parameters:
* Documentation [ReferHere](https://wiki.jenkins.io/display/JENKINS/Parameterized+Build)

![preview](../images/jenkins90.png)

* Install the plugin as shown in below image:
![preview](../images/jenkins91.png)

* After install we can see the option in parameters:
![preview](../images/jenkins92.png)

![preview](../images/jenkins93.png)

![preview](../images/jenkins94.png)

![preview](../images/jenkins95.png)

## Trigger the jenkins jobs from one-job-to-another-job:
* Install the plugin __Parameterized Trigger__ as shown in the below image:
![preview](../images/jenkins97.png)

* Use the __Trigger parameterized build on other projects__ to trigger other job:
    ![preview](../images/jenkins98.png)
    ![preview](../images/jenkins99.png)


## Jenkins Node/slave in jenkins:
* For understanding the node concept. refer below architecture :

![preview](../images/jenkins60.png)

## Basic architecture of jenkins master and node:

![preview](../images/jenkins61.png)

* To add the node to the jenkins as per the above image. Do the ssh-keygen as showm below in jenkins-master:

![preview](../images/jenkins62.png)

## Add node/slave to the jenkins.

* In manage jenkins => mange nodes 

![preview](../images/jenkins63.png)

![preview](../images/jenkins64.png)

![preview](../images/jenkins65.png)

![preview](../images/jenkins66.png)

![preview](../images/jenkins67.png)

## Use node/slave in the jenkins job:

![preview](../images/jenkins68.png)

![preview](../images/jenkins69.png)

## Backup of jenkins:

![preview](../images/jenkins70.png)

![preview](../images/jenkins71.png)

![preview](../images/jenkins72.png)

![preview](../images/jenkins73.png)

![preview](../images/jenkins74.png)


## Restart the jenkins :
* Multiple ways to restart 
  1. In cli 
    ``` 
    sudo service jenkins restart 
    ```
  2. From GUI 
    ![preview](../images/jenkins54.png)
  3. In manage jenkins
     ![preview](../images/jenkins55.png)

## Configurations in the __ Manage jenkins__
* In manage jenkins => configure system 

![preview](../images/jenkins56.png)

![preview](../images/jenkins57.png)

* In manage jenkins => configure global security 

![preview](../images/jenkins58.png)

## Manage Plugins
* In manage jenkins => manage plugins

![preview](../images/jen2.png)

![preview](../images/jenkins71.png)

![preview](../images/jenkins72.png)


# Create a jenkins job in pipeline format:
![preview](../images/jenkins76.png)

![preview](../images/jenkins77.png)


* Basic syntax on the groovy:

```
node('<LABEL>'){
    stage('git clone'){
      
    }
    stage('build the code){

    }
    stage('archive the artifacts'){

    }
    stage('publish the junit reports'){

    }
    stage('Running the ansible playbook'){
        
    }
}
  
```

## Jenkins pipeline :
* In jenkins pipeline there are two ways:
  1. Pipeline  script     -- Scripted pipeline 
  2. Pipeline  script from SCM -- Declarative pipeline

* The approcah we follow for the jenkins pipeline and writing the groovy for is called as pipeline-as-code.

## Basic scripted pipeline :
```
node('ubuntu'){
    stage('git clone'){
      git 'https://github.com/devops-surya/game-of-life.git' 
    }
    stage('build the code'){
      sh 'mvn package'
    }
    stage('archive the artifacts'){
      archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
    }
    stage('publish the junit reports'){
      junit 'gameoflife-web/target/surefire-reports/*.xml'
    }
}
```
## Snippet generator:
![preview](../images/jenkins78.png)

## To generate the pipeline script for git:
![preview](../images/jenkins79.png)

## To generate pipeline for the publish junkts tests:
![preview](../images/jenkins80.png)


* The output of the jenkins pipeline job will be as below:
![preview](../images/jenkins81.png)

## Job Configuration History :
* This plugin is used to tarck the changes made previously  .
![preview](../images/jenkins82.png)

## Jenkinsfile 
* Using jenkins will be helpful in tracking the changes .

## Scripted pipeline vs declarative pipeline :
*  Scripted pipeline:
```
node('ubuntu'){
    stage('git clone'){
      git 'https://github.com/devops-surya/game-of-life.git' 
    }
    stage('build the code'){
      sh 'mvn package'
    }
    stage('archive the artifacts'){
      archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
    }
    stage('publish the junit reports'){
      junit 'gameoflife-web/target/surefire-reports/*.xml'
    }
}
```

* Declarative pipeline:
```
pipeline {
   agent { label 'ubuntu' }
   stages{
       stage('git clone'){
           steps{
               git 'https://github.com/devops-surya/game-of-life.git'  
           }        
       }
       stage('build the code'){
           steps{
              sh 'mvn package'
           }
       }
       stage('archive the artifacts'){
           steps{
              archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
           }          
       }
       stage('publish the junit reports'){
           steps{
              junit 'gameoflife-web/target/surefire-reports/*.xml'
           }
           
       }

   }
}
```

## Create a new pipeline job with pipeline script from scm as below:

![preview](../images/jenkins83.png)
![preview](../images/jenkins84.png)

## Blue ocean plugin :
* In manage jenkins => manage plugins => available => Blue ocean
* After installing u r going to see below changes:
![preview](../images/jenkins85.png)
![preview](../images/jenkins86.png)

* Declarative pipeline:
```
pipeline {
   agent { label 'ubuntu' }
   stages{
       stage('git clone'){
           steps{
               git 'https://github.com/devops-surya/game-of-life.git'  
           }        
       }
       stage('build the code'){
           steps{
              sh 'mvn package'
           }
       }
       stage('archive the artifacts'){
           steps{
              archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
           }          
       }
       stage('publish the junit reports'){
           steps{
              junit 'gameoflife-web/target/surefire-reports/*.xml'
           }
           
       }

   }
}
```

## Create a new pipeline job with pipeline script from scm as below:

![preview](../images/jenkins83.png)
![preview](../images/jenkins84.png)

## Blue ocean plugin :
* In manage jenkins => manage plugins => available => Blue ocean
* After installing u r going to see below changes:
![preview](../images/jenkins85.png)
![preview](../images/jenkins86.png)

## FORK:

![preview](../images/jenkins87.png)

* Go to the repo  which you want to fork:

![preview](../images/jenkins88.png) 

![preview](../images/jenkins89.png)



## SNAPSHOT vs RELEASE 
* If you find the a artifacts with the Snapshot , that means it is still in development.
* If you find your artifact with the release , that means it is ready for the deploymnet and sent it to production.

EX: Game-of-life.war-sanapshot-1.0 
EX: Game-of-life.war-Release-1.0

## Upstream and Downstream projects:
![preview](../images/jenkins100.png)
![preview](../images/jenkins101.png)


## Jenkins declarative pipeline syntax:
* For the pipeline syntax refer the link [REFER HERE](https://www.jenkins.io/doc/book/pipeline/syntax/)

## For git pipeline syatax [REFER HERE](https://www.jenkins.io/doc/pipeline/steps/git/)

```
pipeline {
   agent any
   stages{
       stage('git clone'){
           steps{
               git branch: 'master', url: 'https://github.com/devops-surya/game-of-life.git'
           }        
       }
       stage('build the code'){
           steps{
              sh 'mvn package'
           }
       }
       stage('archive the artifacts'){
           steps{
              archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
           }          
       }
       stage('publish the junit reports'){
           steps{
              junit 'gameoflife-web/target/surefire-reports/*.xml'
           }
           
       }

   }
}
```

## Triggers for build peridically and pollSCM in the pipeline job [REFER HERE](https://www.jenkins.io/doc/book/pipeline/syntax/#triggers)

```
pipeline {
   agent any
   triggers{
      cron('* * * * *')
   }
   triggers{
      pollSCM('* 8 * * *')
   }
   stages{
       stage('git clone'){
           steps{
               git branch: 'master', url: 'https://github.com/devops-surya/game-of-life.git'
           }        
       }
       stage('build the code'){
           steps{
              sh 'mvn package'
           }
       }
       stage('archive the artifacts'){
           steps{
              archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
           }          
       }
       stage('publish the junit reports'){
           steps{
              junit 'gameoflife-web/target/surefire-reports/*.xml'
           }
           
       }

   }
}
```

## UPSTREAM job triggering:

```
pipeline {
   agent any
   triggers{
     upstream(upstreamProjects: 'pipeline-1', threshold: hudson.model.Result.SUCCESS)
   }
   stages{
       stage('git clone'){
           steps{
               git branch: 'master', url: 'https://github.com/devops-surya/game-of-life.git'
           }        
       }
       stage('build the code'){
           steps{
              sh 'mvn package'
           }
       }
       stage('archive the artifacts'){
           steps{
              archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
           }          
       }
       stage('publish the junit reports'){
           steps{
              junit 'gameoflife-web/target/surefire-reports/*.xml'
           }
           
       }

   }
}
```

## Parameters using in jenkins pipeline [REFER HERE](https://www.jenkins.io/doc/book/pipeline/syntax/#parameters)
```
pipeline {
    agent any
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Example') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }
    }
}

```

## Building the another job from this present job [REFER HERE](https://www.jenkins.io/doc/pipeline/steps/pipeline-build-step/)
```
pipeline {
   agent any
   triggers{
     upstream(upstreamProjects: 'pipeline-1', threshold: hudson.model.Result.SUCCESS)
   }
   parameters{
     string(name: 'BUILD_BRANCH', defaultValue: 'master', description: 'parameterized the branch' )
   }
   stages{
       stage('git clone'){
           steps{
               git branch: "$BUILD_BRANCH", url: 'https://github.com/devops-surya/game-of-life.git'
           }        
       }
       stage('build the code'){
           steps{
              sh 'mvn package'
           }
       }
       stage('archive the artifacts'){
           steps{
              archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
           }          
       }
       stage('publish the junit reports'){
           steps{
              junit 'gameoflife-web/target/surefire-reports/*.xml'
           }
	   stage('triggering the another job named gol'){
	       steps{
		      build job: 'gol'
		   }
	   }
           
       }

   }
}
```

## Multibranch pipeline:

![preview](../images/jenkins102.png)

![preview](../images/jenkins103.png)



## Jfrog artifactory :
* To install the jfrog [REFER HERE](https://jfrog.com/open-source/#artifactory)
![preview](../images/jenkins104.png)

* After downloading that , need copy that to the machine where you  want to install artifactory:
 1. In your local machine , copy the jfrog-artifactory-oss-7.10.6.deb to the path documents => mobaxterm => home 
 2. copy to the artifactory machine
    ```
     scp -i <pemfilepath> jfrog-artifactory-oss-7.10.6.deb   ubuntu@<publicip>:/home/ubuntu/
     ```
 3. After copying to the artifactory machine follow below commads:
    ```
    sudo dpkg -i jfrog-artifactory-oss-7.10.6.deb
    systemctl enable artifactory
    sudo systemctl start  artifactory
    ```
  4. Open artifactory in UI
    ```
    http://publicip:8081/artifactory
    ```
    ![preview](../images/jenkins105.png)
  5. Give the username and password.
  ```
  Username: admin
  Password: password
  ```
  ![preview](../images/jenkins106.png)
  * It will ask for change password:
  ![preview](../images/jenkins107.png)

  * To create repositry see below steps:
  ![preview](../images/jenkins108.png)

  ![preview](../images/jenkins109.png)

  ![preview](../images/jenkins110.png)

  ![preview](../images/jenkins111.png)

  6. Make sure that artifactory plugin is installed before doing the jforgintegartion with jenkins
   ![preview](../images/jenkins116.png)

  7. To integrate JFROG with the jenkins , follow below steps:
      Managejenkins => configure system => artifactory
    ![preview](../images/jenkins112.png)
  8. Cretae a maven project by following below steps:
     ![preview](../images/jenkins113.png)
     ![preview](../images/jenkins114.png)
     ![preview](../images/jenkins115.png)
  9. Build the job and check the jfor artifactory repo :
     ![preview](../images/jenkins117.png)

* For the  jforg ansible module  [REFER HERE](https://docs.ansible.com/ansible/latest/collections/community/general/maven_artifact_module.html)

* For the Jfrog to be added in the Jenkinsfile declarative pipeline [REFER HERE](https://www.jfrog.com/confluence/display/RTF6X/Declarative+Pipeline+Syntax)
