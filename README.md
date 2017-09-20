# Severino - O Jenkins faz Tudo

Container docker para subir a ultima versão do Jenkins-CI em alpine utilizando o docker externo, se subir conforme informado.

## Severino

* Baseada no Jenkins lastest Alpine
* Contém os plugins importantes
* Cuidado ! Ele deve terminar com os comandos do user root para não dar permission denied
* Permissões e grupos adicionadas para evitar permission denied
* No Job cria Job, ou Docker dentro de Docker, usa o docker externo

* Rodar conforme abaixo:
```
>docker run -d -v /var/run/docker.sock:/var/run/docker.sock -p 8080:8080 severino
```

* Pipeline de teste abaixo:
```
node {
    def dockerImage
    
    stage('Test') {
        dockerImage = docker.image('hello-world')
        dockerImage.run()
    }
}
```