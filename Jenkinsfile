pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				echo 'Building..'
				echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
温东(28152082)  17:59:15
pipeline {
    agent any 
    stages {
    
        stage('replace file') {
            steps {
                echo "replace config file use cp "
            }
        }
        
        stage('unit test') {
            steps {
                echo "unit test "
            }
        }
        
        stage('package') {
            steps {
                sh 'tar czf  /opt/web-${BUILD_ID}.tar.gz ./* --exclude=./git --exclude=Jenkinsfile'
            }
        }
        
        stage('deploy') {
            steps {
                sh 'ssh 10.0.0.11 "cd /var/www && mkdir web-${BUILD_ID}"'
                sh 'scp /opt/web-${BUILD_ID}.tar.gz 10.0.0.11:/var/www/web-${BUILD_ID}'
                sh 'ssh 10.0.0.11 "cd /var/www/web-${BUILD_ID} && tar xf web-${BUILD_ID}.tar.gz &&rm -f web-${BUILD_ID}.tar.gz"'
                sh 'ssh 10.0.0.11 "cd /var/www && rm -rf html && ln -s /var/www/web-${BUILD_ID}" /var/www/html'
            }
        }
        
        stage('test') {
            steps {
                echo "deploy after test "
            }
        }
    }
}
