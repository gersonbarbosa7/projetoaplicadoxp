# Modernização da Aplicação

## Índice
1. [Introdução](#1-introdução)
2. [Arquitetura](#2-arquitetura)
3. [Padrões de Projeto](#3-padrões-de-projeto)
4. [Back-end](#4-back-end)
5. [Banco de Dados](#5-banco-de-dados)
6. [Front-end](#6-front-end)
7. [DevOps e Infraestrutura](#7-devops-e-infraestrutura)
8. [Segurança](#8-segurança)
9. [Testes](#9-testes)
10. [Manutenção e Suporte](#10-manutenção-e-suporte)

## 1. Introdução
### 1.1 Visão Geral do Projeto
Este projeto visa modernizar uma aplicação legada, originalmente desenvolvida em uma versão antiga de Java, para utilizar tecnologias modernas e melhores práticas. O projeto envolve a migração para um front-end em React.js, back-end em Node.js com TypeScript, e integração com bancos de dados SQL Server e Oracle.

### 1.2 Objetivos
- **Melhorar a escalabilidade e performance da aplicação.**
- **Adotar uma arquitetura de microserviços para maior modularidade.**
- **Implementar práticas de desenvolvimento modernas, incluindo SOLID e CI/CD.**

### 1.3 Tecnologias Utilizadas
- **Front-end:** [React.js](https://reactjs.org/), [TypeScript](https://www.typescriptlang.org/)
- **Back-end:** [Node.js](https://nodejs.org/), [TypeScript](https://www.typescriptlang.org/)
- **Banco de Dados:** [SQL Server](https://www.microsoft.com/en-us/sql-server), [Oracle](https://www.oracle.com/database/)
- **DevOps:** [Terraform](https://www.terraform.io/), [AWS RDS](https://aws.amazon.com/rds/), [EKS Kubernetes](https://aws.amazon.com/eks/)

## 2. Arquitetura
### 2.1 Diagrama de Arquitetura Geral
![Diagrama de Arquitetura](./assets/diagrama-arquitetura.png)

### 2.2 Descrição dos Componentes
- **Front-end:** Implementado em React.js com TypeScript, utilizando hooks personalizados para melhor gerenciamento de estado e reuso de lógica.
- **Back-end:** Construído em Node.js com TypeScript, seguindo os princípios SOLID para garantir um código mais limpo, escalável e fácil de manter.
- **Banco de Dados:** SQL Server para o ambiente de homologação e Oracle para o ambiente de produção, utilizando RDS no AWS para gerenciamento.

### 2.3 Fluxo de Dados
```mermaid
graph LR
  A[Usuário] --> B[Front-end React.js]
  B --> C[Back-end Node.js]
  C --> D[SQL Server/Oracle]
  C --> E[Serviços Externos]
  ```

### 3. Padrões de Projeto

## 3.1 Padrões Utilizados
SOLID: Princípios de design orientado a objetos para garantir um código modular e de fácil manutenção.
Factory: Para criação de objetos complexos, facilitando a extensão e manutenção do código.
Repository: Abstração da camada de acesso a dados, permitindo mudanças no banco de dados sem afetar o restante da aplicação.
3.2 Justificativa para a Escolha dos Padrões
Esses padrões foram escolhidos para garantir que o código seja fácil de entender, modificar, e escalar, além de facilitar a integração com outras partes da aplicação e sistemas externos.

### 4. Back-end

## 4.1 Estrutura do Projeto

├── src
│   ├── controllers
│   ├── models
│   ├── repositories
│   ├── services
│   ├── utils
│   └── index.ts
└── tsconfig.json

### 4.2 Endpoints de API
A documentação completa dos endpoints de API será gerada automaticamente e pode ser acessada aqui.

## 4.3 Fluxo de Autenticação e Autorização
O sistema de autenticação utiliza JWT para garantir segurança nas comunicações e controle de acesso às diferentes funcionalidades da aplicação.

### 4.4 Gerenciamento de Dependências
```json
{
  "dependencies": {
    "express": "^4.17.1",
    "typeorm": "^0.2.34",
    "typescript": "^4.5.2",
    "jsonwebtoken": "^8.5.1"
  }
}
```

### 5. Banco de Dados

## 5.1 Modelo de Dados
5.2 Estrutura de Tabelas
Tabela usuarios:
id: Chave primária.
nome: Nome do usuário.
Tabela pedidos:
id: Chave primária.
usuario_id: Chave estrangeira que referencia usuarios.

## 5.3 Procedimentos Armazenados e Triggers
Descreveremos os procedimentos armazenados e triggers à medida que forem sendo desenvolvidos.

### 6. Front-end

## 6.1 Estrutura do Projeto
├── src
│   ├── components
│   ├── hooks
│   ├── pages
│   ├── services
│   ├── App.tsx
└── index.tsx


## 6.2 Fluxo de Navegação
O fluxo de navegação é gerenciado por React Router, permitindo uma navegação eficiente e modular. Abaixo, um diagrama simplificado de navegação:
```mermaid
graph TD
  Home --> Login
  Login --> Dashboard
  Dashboard --> Settings
  ```


## 6.3 Hooks Personalizados
Estamos utilizando hooks personalizados para encapsular lógicas complexas que são reutilizadas em diferentes componentes, seguindo as melhores práticas de React e TypeScript.

## 6.4 Gerenciamento de Estado
O gerenciamento de estado global está sendo feito com Context API e useReducer, o que proporciona uma abordagem escalável e fácil de manter.

### 7. DevOps e Infraestrutura

## 7.1 Ambientes
Desenvolvimento: Configurado localmente com Docker e banco de dados SQL Server.
Homologação: Ambiente configurado na AWS, utilizando SQL Server via RDS.
Produção: Ambiente de produção com Oracle, configurado em RDS na AWS.
7.2 CI/CD Pipeline
O pipeline de CI/CD foi configurado usando GitHub Actions, com deploy automático para os ambientes de homologação e produção após a aprovação das pull requests.

## 7.3 Deploy e Gerenciamento de Releases
O deploy é feito de forma automatizada, utilizando Kubernetes para gerenciar a escalabilidade da aplicação em produção.

### 8. Segurança

## 8.1 Práticas de Segurança Implementadas
Autenticação: JWT com renovação de tokens e expiração automática.
Autorização: Baseada em roles, definindo permissões específicas para diferentes tipos de usuários.
Criptografia: Uso de TLS/SSL para todas as comunicações entre os serviços.
8.2 Controle de Acesso
O controle de acesso segue uma hierarquia de roles, onde cada usuário tem permissões específicas que definem o que ele pode ou não fazer na aplicação.

### 9. Testes

## 9.1 Estratégias de Teste
Testes Unitários: Cobertura de todas as funções críticas com Jest.
Testes de Integração: Testes das interações entre componentes utilizando Supertest.
Testes End-to-End: Cypress para validar fluxos completos do usuário.

## 9.2 Ferramentas de Teste Utilizadas
Jest: Framework principal para testes unitários.
Cypress: Para testes end-to-end.
Supertest: Para testes de integração das APIs.

### 10. Manutenção e Suporte

## 10.1 Rotinas de Manutenção
Manutenção programada com atualizações de dependências a cada sprint e verificações de segurança.

## 10.2 Monitoramento e Logging
Grafana: Para monitoramento de performance e uptime.
Elasticsearch + Kibana: Para logging centralizado e análise de logs.

## 10.3 Procedimentos de Backup e Recuperação
Procedimentos automatizados de backup diário e recuperação de dados testados mensalmente.