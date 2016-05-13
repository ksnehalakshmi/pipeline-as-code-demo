#!groovy

stage 'Dev'
node {
  checkout scm
  bat 'mvn validate' 
  bat 'mvn compile'
  bat 'mvn test'
  bat 'mvn package'
  
   dir('target') {stash name: 'war', includes: 'x.war'}
}

stage 'approve'
input message: "Does Dev look good?"
