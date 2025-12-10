pipeline {
    agent any

    stages{
        stage('Git repo clone') {
            steps{
                git branch: 'master',
                    url:'https://github.com/AnitaPK/B73-python-pipeline-jenkin.git'
            }
        }
        stage('Create environment') {
            steps {
                bat ''' 
                    python -m venv venv
                     call venv\\Scripts\\activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                 '''
            }
        }
        // stage('Run the test') {
        //     steps {
        //         bat '''
        //             call venv\\Scripts\\activate
        //             pytest -v
        //         '''
        //     }
        // }
         stage('Run Application') {
            steps {
                bat '''
                .call venv\\Scripts\\activate
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