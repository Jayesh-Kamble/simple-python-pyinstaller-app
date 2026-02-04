pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m py_compile sources\\add2vals.py sources\\calc.py'
            }
        }
        stage('Test') {
            steps {
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install pytest pyinstaller'
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pytest --verbose --junitxml=test-reports\\results.xml sources\\test_calc.py'
            }
        }
        stage('Deliver') {
            steps {
                bat '"C:\\Users\\Success\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pyinstaller --onefile sources\\add2vals.py'
            }
        }
    }
}
