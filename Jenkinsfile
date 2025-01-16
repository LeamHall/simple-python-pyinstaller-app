pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py' 
                stash(name: 'compiled-results', includes: 'sources/*.py*') 
            }
        }
        stage('Test') {
            steps {
                sh 'cd sources; python -m unittest; cd ..'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
    }
}


