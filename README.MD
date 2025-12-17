# Laboratório AWS RDS Multi-AZ com MySQL e Aplicação Web

## 📌 Visão Geral
Documentação de um laboratório que demonstra o uso do Amazon RDS (MySQL) em implantação Multi-AZ, com foco em alta disponibilidade, segurança e boas práticas na AWS. O banco de dados é integrado a uma aplicação web hospedada em uma instância EC2, garantindo redundância e tolerância a falhas.

---

## 🎯 Objetivos do Laboratório
Ao final deste laboratório, foi possível:

- Criar uma instância do **Amazon RDS MySQL** com alta disponibilidade (Multi-AZ)
- Configurar **grupos de segurança** para controlar o acesso ao banco de dados
- Criar um **grupo de sub-redes** para o RDS em múltiplas Zonas de Disponibilidade
- Integrar uma aplicação web hospedada em uma instância **EC2** ao banco de dados
- Executar operações de **inserção, edição e remoção de dados (CRUD)** por meio da aplicação web

---

## 🏗️ Arquitetura Utilizada
A arquitetura do laboratório é composta pelos seguintes recursos:

- **Amazon VPC** dedicada ao ambiente do laboratório  
- **Amazon RDS MySQL** em modo Multi-AZ  
- **Grupos de segurança** para controle de tráfego entre EC2 e RDS  
- **Grupo de sub-redes do RDS** distribuído em duas Zonas de Disponibilidade  
- **Instância EC2** executando uma aplicação web de catálogo de endereços  

A comunicação entre a aplicação e o banco de dados ocorre de forma privada e segura dentro da VPC.


## 1️⃣ Criação do Grupo de Segurança

Foi criado um **Security Group** para permitir que o servidor web acesse o banco de dados RDS de forma segura.

### Configurações

- **Nome:** DB Security Group  
- **Descrição:** Permit access from Web Security Group  
- **VPC:** Lab VPC  

### Regra de Entrada

- **Tipo:** MySQL/Aurora (3306)  
- **Origem:** Web Security Group  

Essa regra permite conexões ao banco de dados apenas a partir das instâncias EC2 associadas ao grupo de segurança da aplicação web.

![Criação do Grupo de Segurança](images/1.png)


---

## 2️⃣ Criação do Grupo de Sub-redes do Banco de Dados

Foi criado um **DB Subnet Group** para definir em quais sub-redes o Amazon RDS pode ser provisionado, garantindo disponibilidade em múltiplas Zonas de Disponibilidade.

### Configurações

- **Nome:** DB-Subnet-Group  
- **Descrição:** DB Subnet Group  
- **VPC:** Lab VPC  

### Sub-redes Selecionadas

- **Zonas de Disponibilidade:** us-east-1a e us-east-1b  
- **CIDR das Sub-redes:**  
  - 10.0.1.0/24  
  - 10.0.3.0/24  

Esse grupo de sub-redes foi utilizado na criação da instância RDS na etapa seguinte.

![Criação do Grupo de Sub-redes do RDS](images/2.PNG)
