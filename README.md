#  Arquitetura Serverless AWS – Gerenciamento de Listas  

Este projeto foi desenvolvido com o objetivo de **consolidar conhecimentos em arquitetura na AWS**, aplicando conceitos de **computação serverless**, **segurança**, **escalabilidade** e **boas práticas de design de sistemas em nuvem**.  

A aplicação simula um sistema de **gerenciamento de listas**, onde o usuário pode **criar, editar, listar, buscar, excluir e exportar listas e itens**, com autenticação e persistência de dados totalmente integradas aos serviços da AWS.  

---

## ☁️ Visão Geral da Arquitetura

A arquitetura foi desenhada no **draw.io**, utilizando serviços nativos da **AWS** para garantir um ambiente **escalável, seguro e de baixo custo**.  
Abaixo está o diagrama que representa o fluxo completo da aplicação:

![1B075BAF-BB8F-43E0-BB09-B882182BB8E2](https://github.com/user-attachments/assets/850b908f-bf56-49a2-8ba8-e5b638cdff56)


---

##  Fluxo Geral

1. O **usuário** acessa o **frontend** (aplicação web) hospedado no **Amazon S3**, distribuído por uma **CDN (CloudFront)**.  
2. O **Amazon Cognito** gerencia a **autenticação e autorização** do usuário, emitindo **tokens JWT**.  
3. As requisições são encaminhadas para o **Amazon API Gateway**, que valida o token e aciona as **funções AWS Lambda**.  
4. As **funções Lambda** realizam as operações de CRUD nas listas e itens.  
5. Os dados são armazenados no **Amazon DynamoDB**, e relatórios em formato CSV são gerados e salvos no **Amazon S3**.  

---

##  Componentes Principais e Funcionalidades

###  Frontend – Amazon S3 + CDN (CloudFront)
O **Amazon S3** armazena o **site estático** (HTML, CSS, JS), enquanto o **Amazon CloudFront** atua como **rede de distribuição de conteúdo (CDN)**.  
Essa combinação garante:  
- **Baixa latência** e **alta performance** no carregamento;  
- **Alta disponibilidade** global;  
- **Segurança via HTTPS** e integração com AWS WAF.  

 **Função:** exibir a interface do usuário e entregar o conteúdo de forma rápida e segura.  

---

###  Amazon Cognito – Autenticação e Autorização
O **Amazon Cognito** gerencia o **cadastro, login e controle de acesso** dos usuários.  
Ele gera **tokens JWT** que são validados pelo **API Gateway** antes de permitir o acesso às **funções Lambda**.  

 **Função:** autenticar usuários, proteger rotas e manter o acesso seguro às APIs.  

---

###  Amazon API Gateway – Gerenciamento de Requisições
O **Amazon API Gateway** atua como **porta de entrada** para todas as requisições do front-end.  
Ele:  
- Valida os tokens do Cognito;  
- Redireciona requisições para as Lambdas corretas;  
- Implementa políticas de segurança, limites de requisições e CORS.  

 **Função:** orquestrar o tráfego entre o front-end e o backend (Lambdas).  

---

###  AWS Lambda – Lógica de Negócio Serverless
As **funções Lambda** executam toda a **lógica da aplicação**, sem a necessidade de servidores.  
Cada função é independente e responsável por uma operação específica:  

-  **Cadastrar nova lista**  
-  **Listar listas**  
-  **Buscar lista por ID**  
-  **Editar lista**  
-  **Cadastrar item na lista**  
-  **Listar itens da lista**  
-  **Editar item da lista**  
-  **Excluir item da lista**  
-  **Gerar CSV da lista**

 **Função:** processar e executar as operações do sistema sob demanda, com escalabilidade automática e custo por uso.  

---

###  Amazon DynamoDB – Banco de Dados NoSQL
O **Amazon DynamoDB** armazena as **listas e itens**, oferecendo:  
- **Alta performance e baixa latência**;  
- **Escalabilidade automática**;  
- **Integração nativa com Lambda** via SDK da AWS.  

 **Função:** persistir os dados de forma rápida, segura e escalável.  

---

###  Amazon S3 – Armazenamento de Arquivos
Além do frontend, o **Amazon S3** também é usado para armazenar os **arquivos CSV** gerados pelas Lambdas.  
Esses arquivos podem ser baixados posteriormente pelo usuário.  

 **Função:** guardar e disponibilizar relatórios e arquivos gerados pela aplicação.  



---

## Reflexão Pessoal

Este laboratório me permitiu:

Consolidar conceitos essenciais da AWS.

Entender na prática como funcionam Lambda e demais serviços.

Criar um ambiente reprodutível, escalável e seguro.

Aumentar minha familiaridade com a Cloud AWS.


---

##  Conclusão

Este projeto foi idealizado pensando na **arquitetura AWS** e na aplicação prática dos seus principais componentes.  
Cada serviço foi escolhido para desempenhar um papel específico dentro da arquitetura serverless, garantindo **segurança, escalabilidade e eficiência**.  

> 💬 “A ideia foi criar uma solução enxuta, segura e escalável — aplicando na prática os principais pilares da arquitetura em nuvem.”  

---
