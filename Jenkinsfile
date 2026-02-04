pipeline {
    agent any

    stages {

        stage('Setup') {
            steps {
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install --upgrade pip'
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install pytest pyinstaller'
            }
        }

        stage('Build') {
            steps {
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m py_compile sources\\add2vals.py sources\\calc.py'
            }
        }

        stage('Test') {
            steps {
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pytest --verbose --junit-xml test-reports\\results.xml sources\\test_calc.py'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }

        stage('Deliver') {
            steps {
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pyinstaller --onefile sources\\add2vals.py'
            }
            post {
                success {
                    archiveArtifacts 'dist\\add2vals.exe'
                }
            }
        }
    }
}
