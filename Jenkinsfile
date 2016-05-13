#!groovy

stage 'Dev'
node {
  checkout scm
  
  bat 'mvn clean install'
  
   dir('target') {stash name: 'war', includes: 'x.war'}
}

stage 'approve'
input message: "Does staging look good?"
