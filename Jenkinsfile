pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '/Users/voyager/Projects/AIOPs/bin/python -m py_compile sources/add2vals.py sources/calc.py'
                stash(name: 'compiled-results', includes: 'sources/*.py*')
            }
        }
        stage('Test') { 
            steps {
                sh '/Users/voyager/Projects/AIOPs/bin/py.test --junit-xml test-reports/results.xml sources/test_calc.py' 
            }
            post {
                always {
                    junit 'test-reports/results.xml' 
                }
            }
        }
    }
}
