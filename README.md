# Deploy do Modelo de Machinee Learning com TensorFlow Serving e Kubernets na nuvem Google Cloud Platform.

[![NPM](https://img.shields.io/npm/l/react)](https://github.com/pand-eX/Deploy_Kubernets/blob/main/LICENSE) 

# Sobre o Projeto.

Basicamente o objetivo e realizar o Deploy do Modelo de Machine Learning com TensorFlow Serving e Kubernets.
O Objetivo é servir um modelo de Machne Learning para reconhecimento de imagens através de Inteligência Artificial. Usaremos o TensorFlow Serving para servir o modelo em um contêiner Docker e faremos o deploy em um cluster Kubernetes para escalabilidade da aplicação, claro o foco aqui vai ser o Deploy e não o modelo, o modelo será pré-treinado e então farei todo o trabalho de infraestrutura para o deploy desse modelo. Depois que o modelo estiver pronto e disponível no container Docker então farei o deploy em um cluster Kubernets e para isso vou utilizar o Google Cloud Platform.


## Porque? 

preciso garantir que o modelo esteja funcionando o tempo todo e queos usuários tenham uma maneira fácil de interagir com o modelo. Ele também deve funcionar bem em todas as plataformas, seja web, Android, IOS ou sistemas embarcados. Precisamos ter um pipeline resiliente para atender ao seu modelo e uma maneira eficiente de transmitir dados.


-Este projeto faz parte do meu portfólio pessoal, então ficarei feliz se você puder me fornecer qualquer feedback sobre o projeto, código, estrutura ou qualquer coisa que você possa relatar que possa me fazer um melhor engenheiro de dados!

Email-me: henricao_7@yahoo.com.br

Connect with me at [LinkedIn](https://www.linkedin.com/in/henrique-castro-484269203//).

## Projeto


![1]()

Todos os Script em Anexo no projeto.

Na prática o que nós fazemos é iniciar o container gravamos o conteúdo dentro do container eu faço um commit e gero uma nova imagem com essa nova imagem eu então vou realizar um outro container e esse sim será usado para servir o modelo

![2]()

finalizamos a etapa que é a configuração do tensorflow/serving eu posso servir o modelo nesse exato momento, mas vou dar um passo adiante e configurar um cluster Kubernets no ambiente em nuvem da google cloud plataform para orquestração do container.

Mas antes o que é Kubernets?

Ele nada mais é que um software que permite você orquestrar, gerenciar, usar da melhor maneira possível os containers para que você possa publicar as aplicações. 

Kubernets é um sistema de orquestração de contêiner de código aberto para automatizar a implantação, dimensionalmento e gerenciamento de aplicativos de computador. Ele foi originalmente projeto pelo Google e agora é mantido pela Cloud Native Computing Foundation.  

O Kubernets surgiu como plataforma de orquestração, sendo ferramenta essencial para equips de Engenharia de Dados. Sua importância é cada vez maior na infraestrutura de Big Data e no Deploy de Modelos de Machine Learning.

![3]()

O Kubernets gerencia o acesso aos contêineres, gerenciando o balanceamento de carga entre os contêineres e automatizando o processo de escalabilidade para as aplicações.

![4]()

![5]()


## Funcionamento do Kubernetes.

Nossa Aplicações serão colocas em contêineres(como fizemos com o modelo de Machine Learning). O Kubernetes vai distribuir os contêineres em Pods, que são estruturas lógicas para as quais atribuímos endereço ip. Qualquer conteiner no mesmo pod compartilhará os mesmo recursos e rede local.

![6]()


Usando os conceitos descrito anteriormente, você pode criar um cluster de nodes e iniciar implatações de pds no cluster. Há um último problema a ser resolvido: permitir o tráfego externo para o aplicativo.
Por padrão, o kubernetes fornece isolamento entre os pds e o mundo externo. Se você deseja se comunicar com um serviço em execução em um pod, é necessário abrir um canal para comunicação. Isso é chamado de Ingress.


Depois de deixar o Gcloud SDK devidamente configurado. 

![7]()

agora vamos instalar e configurar o Kubectl que é uma espécie de gerenciamento do Kubernets e ai estaremos pronto para definir o cluster Kubernets e fazer o Deploy.
Já temos o Google Cloud SDK o conjunto de ferramentas de linha de comando para acessar remotamente o ambiente em nuvem da Google o GCP. Agora precisamos de ferramenta para gerenciar o Kubernets por isso o Kubectl.

![8]()

Agora já temos o Kubectl só precisamos ativar o engine API do Kubernets lá no Google Plataform.


![9]()

Pronto Cluster Criado.

![10]()

Cluster Kubernets está pronto.
Deploy do modelo no kubernetes.

![11]()

Agora é fazer a configuração do serviço de acesso a nossa aplicação do cluster Kubernets. Ninguém na internet consegue acessa a nossa aplicação lá no cluster kubernets, precisamos de mais uma etapa. Agora vamos criar o serviço já fazendo o load balace de modo que automaticamente o Kubernets gerencie o balanceamento de carga.

![12]()

Criado com sucesso.


![13]()

Fazendo 10 previsões. Cada linha dessa é uma previsão de reconhecimento de imagem, ao invés de mostrar a imagem estou mostrando o tempo de execução.
