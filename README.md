# Gerenciando-Inst-ncias-EC2-na-AWS
#  Projeto: Consolidação em Gerenciamento de Instâncias EC2 na AWS

##  Descrição do Projeto

Este projeto tem como objetivo **consolidar o entendimento e a prática do gerenciamento de instâncias EC2 na AWS**, abordando conceitos fundamentais de infraestrutura em nuvem.  
O diagrama foi desenvolvido no **Draw.io**, representando uma **arquitetura simplificada em ambiente AWS**, incluindo os principais serviços relacionados à computação, armazenamento e banco de dados.

---

## ☁️ Arquitetura do Projeto

A estrutura deste projeto foi projetada para demonstrar o fluxo e a relação entre os principais componentes da AWS em um cenário prático de uso.  
O diagrama mostra como uma instância EC2 interage com volumes EBS, usuários e um banco de dados RDS.

### **Componentes Principais:**

- **Amazon EC2 (Elastic Compute Cloud)**  
  Instância configurada para executar aplicações em ambiente Linux.  
  Responsável pelo processamento principal e hospedagem dos serviços da aplicação.

- **Amazon EBS (Elastic Block Store)**  
  Dois volumes EBS foram adicionados:  
  - **EBS 1:** Volume principal (sistema operacional).  
  - **EBS 2:** Volume secundário (armazenamento de dados e backups).  
  Ambos conectados à instância EC2, garantindo persistência e escalabilidade de armazenamento.

- **Amazon RDS (Relational Database Service)**  
  Banco de dados relacional utilizado para armazenar dados da aplicação.  
  Configurado com segurança e acesso controlado apenas pela instância EC2 e pelo usuário autorizado.

- **Usuário AWS**  
  Usuário IAM com permissões definidas para gerenciamento das instâncias EC2, volumes EBS e RDS.  
  As políticas de acesso foram configuradas seguindo o princípio de **menor privilégio**.

---

## ⚙️ Processos Técnicos Documentados

1. **Criação e Configuração da Instância EC2**  
   SO: Amazon Linux 2

  Tipo: t2.micro (Free Tier)

  Configurações:

  -Porta 22 (SSH) liberada
  -Porta 80 (HTTP) liberada
  -Volume EBS de 8 GB
  
  <img width="1920" height="859" alt="496347839-9c087134-1aad-4415-b613-c1acc3b43b53" src="https://github.com/user-attachments/assets/b616abd4-3843-4465-afc0-5911835267a9" />


2. **Instância em Execução**

Após o deploy, a instância entrou em estado Running. 

<img width="1920" height="860" alt="496347665-b69bd9d5-ab54-42e7-8150-b90d6552d332" src="https://github.com/user-attachments/assets/85aca74c-d0de-41b4-9e5f-d6c5ec21b6cd" />


3.  **Criação da AMI**

Após personalizar a instância, foi criada uma Amazon Machine Image (AMI) personalizada.

4. **Criação de Snapshot EBS**

Snapshot do volume EBS criado como backup e ponto de restauração.

5. **Nova Instância a partir da AMI**

Uma nova instância foi lançada com base na AMI personalizada para validar sua integridade.



---

## 🗂️ Ferramenta de Diagramação

O **diagrama da arquitetura** foi desenvolvido no **[Draw.io](https://app.diagrams.net/)**, com foco em clareza e boa representação visual dos fluxos de comunicação entre os serviços AWS.

📁 O arquivo do diagrama (.drawio) está disponível neste repositório para visualização .

---

## 🧠 Aprendizados e Objetivos

- Compreensão prática sobre o funcionamento de instâncias EC2 e seus volumes de armazenamento.  
- Integração entre serviços da AWS (EC2 + EBS + RDS).  
- Aplicação de boas práticas em gerenciamento de usuários e segurança (IAM).
- Funcionalidade da AWS AMI.
- Desenvolvimento da capacidade de documentar arquiteturas técnicas de forma clara e profissional.  

---

## 📌 Tecnologias e Serviços Utilizados

- **AWS EC2**  
- **AWS EBS**  
- **AWS RDS**
- **AWS AMI**  
- **AWS IAM**  
- **Draw.io**
---


Este projeto é de uso **educacional** e, criado com o propósito de aprendizado e demonstração de conceitos de Cloud Computing na AWS.
