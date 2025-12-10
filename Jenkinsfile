pipeline {
    agent any

    statges{
        stage 'Git repo clone' {
            steps{
                git branch: 'master',
                    url:'https://github.com/AnitaPK/B73-python-pipeline-jenkin.git'
            }
        }
        stage 'Create environment' {
            steps {
                bat ''' 
                    python -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                 '''
            }
        }
        stage 'Run the test' {
            steps {
                bat '''
                    . venv/bin/activate
                    pytest -v
                '''
            }
        }
         stage('Run Application') {
            steps {
                bat '''
                . venv/bin/activate
                python app/main.py
                '''
            }
         }
    }
    post {
        always {
            echo 'Pipeline completed!!!'
        }
    }
}