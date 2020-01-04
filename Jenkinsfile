node {
    def app

    stage('Clonar repositorio') {
         
        checkout scm
    }

    stage('Buildar imagem do docker') {

        app = docker.build("hodestito/devops_aula5")
    }

    stage('Push da imagem para o Dockerhub') {

        docker.withRegistry('https://registry.hub.docker.com', 'credenciais-dockerhub') {
            app.push("latest")

        }
    }

    stage('Deploy do container via ansible-playbook') {

        //ansiblePlaybook(
        //    playbook: 'playbook.yml'
        //)
        sh 'ansible-playbook playbook.yml'

    }
}
