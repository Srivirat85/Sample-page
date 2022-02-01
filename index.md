## Jenkins

Jenkins is a self-contained, open source automation server which can be used to automate all sorts of tasks related to building, testing, and delivering or deploying software.

Jenkins can be installed through native system packages, Docker, or even run standalone by any machine with a Java Runtime Environment (JRE) installed.

### What is Jenkins Pipeline?

Jenkins Pipeline (or simply "Pipeline" with a capital "P") is a suite of plugins which supports implementing and integrating continuous delivery pipelines into Jenkins.
Creating a Jenkinsfile and committing it to source control provides a number of immediate benefits:

- Automatically creates a Pipeline build process for all branches and pull requests.

- Code review/iteration on the Pipeline (along with the remaining source code).

- Audit trail for the Pipeline.

- Single source of truth for the Pipeline, which can be viewed and edited by multiple members of the project.

- While the syntax for defining a Pipeline, either in the web UI or with a Jenkinsfile is the same, it is generally considered best practice to define the Pipeline in a Jenkinsfile and check that in to source control.

The flowchart below is an example of one CD scenario easily modeled in Jenkins Pipeline:
![image](https://user-images.githubusercontent.com/94677918/151970164-244f05fa-804c-44f6-bce6-7cd4486e50e1.png)

### Pipeline syntax overview:
The following Pipeline code skeletons illustrate the fundamental differences between Declarative Pipeline syntax and Scripted Pipeline syntax.

Be aware that both stages and steps (above) are common elements of both Declarative and Scripted Pipeline syntax.

### Declarative Pipeline fundamentals
In Declarative Pipeline syntax, the pipeline block defines all the work done throughout your entire Pipeline.

```markdown
### Jenkinsfile (Declarative Pipeline)
pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                // 
            }
        }
        stage('Test') { 
            steps {
                // 
            }
        }
        stage('Deploy') { 
            steps {
                // 
            }
        }
    }
}
```
1. Execute this Pipeline or any of its stages, on any available agent.
2. Defines the "Build" stage.
3. Perform some steps related to the "Build" stage.
4. Defines the "Test" stage.
5. Perform some steps related to the "Test" stage.
6. Defines the "Deploy" stage.
7. Perform some steps related to the "Deploy" stage.

### Scripted Pipeline fundamentals
In Scripted Pipeline syntax, one or more node blocks do the core work throughout the entire Pipeline. Although this is not a mandatory requirement of Scripted Pipeline syntax, confining your Pipeline’s work inside of a node block does two things:

1. Schedules the steps contained within the block to run by adding an item to the Jenkins queue. As soon as an executor is free on a node, the steps will run.

2. Creates a workspace (a directory specific to that particular Pipeline) where work can be done on files checked out from source control.

```markdown
### Jenkinsfile (Scripted Pipeline)
node {  
    stage('Build') { 
        // 
    }
    stage('Test') { 
        // 
    }
    stage('Deploy') { 
        // 
    }
}
```
1. 	Execute this Pipeline or any of its stages, on any available agent.
2. Defines the "Build" stage. stage blocks are optional in Scripted Pipeline syntax. However, implementing stage blocks in a Scripted Pipeline provides clearer visualization of each `stage’s subset of tasks/steps in the Jenkins UI.
3. Perform some steps related to the "Build" stage.
4. Defines the "Test" stage.
5. Perform some steps related to the "Test" stage.
6. Defines the "Deploy" stage.
7. Perform some steps related to the "Deploy" stage.

### Usage

In order to run the Jenkins locally using docker,
1. Copy the Dockerfile_jenkins_master to local as Dockerfile
2. BuildImage using : docker build -t IMAGE_NAME .
3. Run the Image using : docker run -d -p 8080:8080 IMAGE_NAME
Now enter a UI to check at http://localhost:8080, that all run successfully.


