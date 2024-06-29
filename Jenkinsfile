pipeline {
    agent any
    stages {
        stage('Копирование'){
            steps {
                git 'https://github.com/IvanovaElizaveta23/AMO2.git'
            }
        }
        stage('Installing dependencies'){ 
            steps {
                script{
                    sh 'python3 -m venv venv'
                    sh 'venv/bin/pip install pandas scikit-learn joblib ucimlrepo'
                }
            }
        }
        stage('Загрузка данных'){
            steps {
                script{
                    sh 'venv/bin/python data_creation.py'
                }
            }
        }
        stage('Предобработка данных'){
            steps {
                script{
                    sh 'python3 -m venv venv'
                    sh 'venv/bin/python data_preprocessing.py'
                }
            }
        }
        stage('Обучение модели'){
            steps {
                script{
                    sh 'venv/bin/python model_preparation.py'
                }
            }
        }
        stage('Предсказание'){
            steps {
                script{
                    sh 'venv/bin/python model_testing.py'
                }
            }
        }
    }
}
