pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'sh \'mvn package\''
      }
    }

    stage('dockerimage') {
      steps {
        sh '''echo "from centos" > Dockerfile
echo "run yum install httpd -y" >> Dockerfile

docker build -t docker .
'''
      }
    }

    stage('deploy') {
      steps {
        sh 'docker run -itd --name ddd -p 99:80 docker '
      }
    }

  }
}