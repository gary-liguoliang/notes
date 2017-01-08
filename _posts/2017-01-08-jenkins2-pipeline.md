---
layout: post 
title: Pipeline as code&#58; Jenkins2 with Pipeline and BlueOcean
tags:
 - Jenkins
 - CI
 - CD
---

**A new(better) way to do CI/CD**

instead of `FreeStyle` jobs, let's try the pipeline as code:
I created a new `Pipeline` project with the fllowing code: 
```
node {
   stage ('Check out') {
        sh name:"print date", script: 'date', label: "Current date"
        sh 'rm -rf dev'
        sh 'mkdir dev'
        dir('dev') {
            git url: "https://github.com/guoliang-dev/bdd-python-example.git"    
        }

        sh 'ls -al dev'
   }
   
   stage ('Build') {
        echo 'Hello World 2'
        
        parallel (
            phase1: { sh "echo p1; sleep 20s; echo phase1" },
            phase2: { sh "echo p2; sleep 40s; echo phase2" }
        )
   }
   
   stage('Deploy') {
       echo 'deploy'
   }
}
```

![jenkins2-pipeline-blueocean](https://raw.githubusercontent.com/guoliang-dev/notes/gh-pages/_resources/jenkins2-pipeline-blueocean.png)
