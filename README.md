# aws-crud-clients-s3-lambda-dynamodb
Aplicação CRUD de clientes hospedada no Amazon S3 com backend serverless usando AWS Lambda, API Gateway e DynamoDB — totalmente dentro do Free Tier da AWS.

## 🧭 Introdução

Este projeto foi desenvolvido com o objetivo de **criar um sistema completo de cadastro de clientes (CRUD)** utilizando **serviços 100% serverless da AWS**, dentro do **Free Tier**.  

O foco principal foi compreender, na prática, como integrar **frontend, backend e banco de dados** em uma arquitetura sem servidores, usando apenas serviços gerenciados pela Amazon Web Services (AWS).  

### 🔧 Serviços utilizados

- **Amazon S3** → Hospedagem do site frontend (HTML, CSS e JavaScript)  
- **AWS Lambda** → Backend sem servidor, responsável pelas operações CRUD  
- **Amazon API Gateway** → Ponto de entrada das requisições HTTP do frontend  
- **Amazon DynamoDB** → Banco de dados NoSQL para armazenar as informações dos clientes  
- **AWS IAM** → Controle de permissões entre os serviços  

---

## 🛠️ Desenvolvimento do Projeto

### 🖥️ 1. Frontend (Amazon S3)

O **frontend** foi criado com HTML, CSS e JavaScript puros, oferecendo uma interface simples para **adicionar, listar, editar e deletar clientes**.  

O site foi hospedado no **Amazon S3**, utilizando o recurso **Static Website Hosting**, o que permite disponibilizar páginas HTML de forma pública e gratuita dentro do Free Tier.  

**Tela do site hospedado:**
  <img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20site%20no%20navegador.jpeg">
**Configuração de Bucket:** 
  <img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20URL%20Publica%20S3.jpeg">

---

### ⚙️ 2. Backend (AWS Lambda)

O **backend** foi implementado em **Node.js 20** e hospedado em uma função **AWS Lambda** chamada `createClient`. 

**Função Criada:**
<img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20Fun%C3%A7%C3%A3o%20Lambda%20Criada.jpeg">

Essa função foi programada para responder a **quatro métodos HTTP diferentes**:
- `GET` → Listar todos os clientes  
- `POST` → Adicionar um novo cliente  
- `PUT` → Atualizar um cliente existente  
- `DELETE` → Remover um cliente pelo ID  

A função se conecta diretamente ao **DynamoDB**, executando as operações de leitura e escrita conforme o método recebido.  

**Codigo Backend Na Lambda:**
<img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20codigo%20backend.jpeg">

**Teste da Função:**
<img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20teste%20da%20fun%C3%A7%C3%A3o.jpeg">

---

### 🌐 3. API Gateway

O **API Gateway** foi utilizado como intermediário entre o frontend e a Lambda.  

Ele atua como um “porteiro”, recebendo as requisições HTTP vindas do site e redirecionando para a função Lambda correta.  

Foi criada uma rota principal `/clientes` com os métodos:
- `GET`, `POST`, `PUT`, `DELETE`  
Todos apontando para a mesma função `createClient`.

**API Criada:** 
<img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20API%20criada.jpeg">

**Integração da API:**

<img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20Integra%C3%A7%C3%A3o%20da%20API.jpeg">

**Invoke URL:**

<img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20Invoke%20URL.jpeg">
---

### 🗄️ 4. Banco de Dados (DynamoDB)

O **Amazon DynamoDB** foi o banco escolhido por ser totalmente gerenciado e escalável, sem necessidade de configurar servidores.  

A tabela foi chamada de **`Clientes`**, com o campo principal:
- **`ID` (String)** → chave primária  

Outros atributos armazenados:
- `nome`  
- `email`  
- `telefone`  

**Tabela Criada:**

 <img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20Tabela%20criada.jpeg">

 **Itens na Tabela:**
 
  <img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20tabela%20clientes.jpeg">
  
--- 

---

### 🔐 5. Permissões (IAM)

Foi criada uma **Role IAM** para a função Lambda, concedendo acesso apenas aos serviços necessários (DynamoDB e CloudWatch).  

Essa etapa foi essencial para garantir **segurança e boas práticas** no uso da AWS.

**Role Criada:**

 <img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/Captura%20de%20tela%20Role%20IAM.jpeg">
---

## 📊 Arquitetura Final

<img src="https://github.com/cauafreirealves/aws-crud-clients-s3-lambda-dynamodb/blob/main/diagramaAWS.png">
---

## ✅ Conclusão

O projeto **CRUD Serverless AWS - Gerenciamento de Clientes** demonstrou na prática como é possível construir uma aplicação **completa, escalável e sem servidores** utilizando serviços nativos da AWS.  

Durante o desenvolvimento, foi possível praticar:
- Criação e deploy de funções Lambda  
- Integração via API Gateway  
- Manipulação de dados com DynamoDB  
- Hospedagem estática no S3  
- Configuração de permissões IAM  

> ⚠️ Observação:  
> Todos os recursos foram criados dentro da **AWS Free Tier** e posteriormente desativados para evitar consumo de créditos.  



## ✍️ Autor

**Cauã Freire Alves**  
Estudante de Análise e Desenvolvimento de Sistemas | Foco em Cloud Computing e AWS  
[LinkedIn](https://www.linkedin.com/in/cauafreirealves)

---

## 🧾 Licença

Este projeto é open-source e pode ser utilizado livremente para fins de estudo.

---


