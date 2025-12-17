# Laboratório AWS RDS Multi-AZ com MySQL e Aplicação Web

## 📌 Visão Geral
Este repositório contém a documentação e o contexto prático de um laboratório voltado ao uso do **Amazon Relational Database Service (RDS)** para a criação e integração de um banco de dados relacional gerenciado na AWS. O objetivo principal foi demonstrar como provisionar uma instância de banco de dados altamente disponível e conectá-la a uma aplicação web hospedada em uma instância **EC2**, seguindo boas práticas de segurança e arquitetura em nuvem.

O laboratório utiliza o mecanismo **MySQL** em uma implantação **Multi-AZ**, garantindo redundância, tolerância a falhas e maior confiabilidade para aplicações que dependem de persistência de dados.

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
