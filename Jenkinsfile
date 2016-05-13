#!groovy

stage 'Dev'
node {
  checkout scm
  
  bat 'mvn clean install'
  
   dir('target') {stash name: 'war', includes: 'x.war'}
}

input message: "Does staging look good?"
