# 📅 New Agenda 2.0

Sistema de agenda eletrônica desenvolvido em **PHP**, com o objetivo de praticar o desenvolvimento de aplicações web com **PHP, MySQL, sessões, autenticação de usuários e organização de páginas**.

O projeto possui uma área de login e cadastro de usuários. Após realizar o login corretamente, o usuário é direcionado para a área interna da agenda.

---

## 📌 Sobre o projeto

O **New Agenda 2.0** é um sistema web de agenda desenvolvido para organizar o acesso de usuários e disponibilizar uma área interna para gerenciamento da aplicação.

O sistema utiliza autenticação por e-mail e senha. As informações dos usuários são armazenadas em um banco de dados MySQL, e as sessões do PHP são utilizadas para controlar o acesso às páginas internas.

O projeto também utiliza o **AdminLTE** como base visual para a interface administrativa.

---

## ⚙️ Como o projeto funciona

O funcionamento principal do sistema segue este fluxo:

```text
                    ┌─────────────────┐
                    │     Sistema     │
                    │  New Agenda 2.0 │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  Tela de Login  │
                    └────────┬────────┘
                             │
                 ┌───────────┴───────────┐
                 │                       │
                 ▼                       ▼
          Já possui conta?          Não possui?
                 │                       │
                 ▼                       ▼
          E-mail + senha          Cadastro de usuário
                 │                       │
                 └───────────┬───────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Banco de Dados  │
                    │     MySQL       │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Autenticação    │
                    │   do usuário    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Área interna da │
                    │     Agenda      │
                    └─────────────────┘
```

### 🔐 Login

Na tela inicial, o usuário informa:

* E-mail
* Senha

O sistema consulta o banco de dados para verificar se o usuário existe.

A senha armazenada no banco é verificada utilizando `password_verify()`.

Quando o login é realizado com sucesso, são criadas variáveis de sessão para identificar o usuário autenticado.

Depois disso, o usuário é encaminhado para:

```text
paginas/home.php?acao=bemvindo
```

Caso o e-mail ou a senha estejam incorretos, o sistema apresenta uma mensagem informando o erro.

---

## 👤 Cadastro

Usuários que ainda não possuem uma conta podem acessar a página de cadastro através do link disponível na tela de login.

O cadastro permite inserir os dados necessários para criar um novo usuário no sistema.

As informações são armazenadas no banco de dados utilizado pela aplicação.

---

## 🗄️ Banco de dados

O projeto utiliza **MySQL** para armazenamento das informações.

O arquivo:

```text
new_agenda.sql
```

contém a estrutura do banco de dados utilizada pelo projeto.

A conexão com o banco de dados é organizada dentro da pasta:

```text
config/
```

---

## 🛡️ Sessões

O projeto utiliza as sessões do PHP para controlar o acesso dos usuários.

Ao realizar o login corretamente, o sistema cria informações na sessão, permitindo identificar o usuário enquanto ele navega pela área interna.

Isso permite separar:

```text
Usuário não autenticado
        ↓
     Login
        ↓
Usuário autenticado
        ↓
Área interna
```

---

## 🧰 Tecnologias utilizadas

### Front-end

* HTML5
* CSS3
* Bootstrap
* AdminLTE
* Font Awesome

### Back-end

* PHP
* PDO
* Sessões PHP

### Banco de dados

* MySQL

### Ferramentas

* Apache
* Git
* GitHub

---

## 📁 Estrutura do projeto

A estrutura principal do projeto está organizada da seguinte maneira:

```text
agendaphp/
│
├── config/
│   └── conexao com o banco de dados
│
├── dist/
│   ├── css/
│   └── js/
│
├── img/
│   └── imagens utilizadas no sistema
│
├── includes/
│   └── arquivos reutilizados pelas páginas
│
├── paginas/
│   └── páginas da área interna da agenda
│
├── plugins/
│   └── bibliotecas e recursos utilizados pela interface
│
├── cad_user.php
├── index.php
├── new_agenda.sql
└── README.md
```

---

## 🚀 Como executar o projeto

Para executar o projeto localmente, é necessário possuir um ambiente com **Apache, PHP e MySQL**.

### 1. Clonar o projeto

```bash
git clone https://github.com/Biancawe8/agendaphp.git
```

Entre na pasta:

```bash
cd agendaphp
```

---

### 2. Colocar o projeto no servidor

Em um ambiente Linux com Apache, o projeto pode ser colocado dentro de:

```text
/var/www/html/
```

Por exemplo:

```text
/var/www/html/agendaphp/
```

---

### 3. Criar o banco de dados

Abra o **phpMyAdmin** e crie o banco de dados utilizado pelo projeto.

Depois, importe o arquivo:

```text
new_agenda.sql
```

Esse arquivo contém as estruturas necessárias para o banco de dados.

---

### 4. Configurar a conexão

Verifique o arquivo:

```text
config/conexao.php
```

e configure os dados de acesso ao MySQL de acordo com o seu ambiente local.

---

### 5. Iniciar o Apache e o MySQL

Certifique-se de que os serviços necessários estejam funcionando.

Depois, abra o projeto no navegador através do endereço correspondente ao seu servidor local.

Exemplo:

```text
http://localhost/agendaphp/
```

---

## 🔑 Fluxo de autenticação

O arquivo principal `index.php` funciona como a tela de login.

O usuário informa seu e-mail e senha e o sistema consulta a tabela de usuários no banco.

A consulta utiliza PDO e parâmetros preparados.

Depois de encontrar o usuário, a senha informada é comparada com a senha armazenada utilizando:

```php
password_verify()
```

Quando a autenticação é válida, o sistema cria a sessão e redireciona o usuário para a área interna.

---

## 📚 Objetivos acadêmicos

Este projeto foi desenvolvido como prática de conceitos de desenvolvimento web, incluindo:

* Desenvolvimento de páginas com PHP
* Formulários HTML
* Conexão entre PHP e MySQL
* Utilização de PDO
* Cadastro de usuários
* Sistema de login
* Autenticação
* Sessões PHP
* Organização de arquivos
* Utilização de Bootstrap
* Utilização do AdminLTE
* Estruturação de um projeto web
* Versionamento utilizando Git e GitHub

---

## 🔒 Segurança

O projeto utiliza alguns mecanismos importantes para autenticação, como:

* `password_verify()` para verificar senhas;
* PDO para comunicação com o banco;
* sessões PHP para controle do usuário autenticado;
* parâmetros preparados nas consultas SQL.

Em um projeto de produção, ainda poderiam ser adicionadas outras camadas de segurança e validação.

---

## 📄 Licença

Este projeto possui um arquivo de licença **MIT** no repositório.

---

## 👩‍💻 Projeto

**New Agenda 2.0**

Desenvolvido como projeto acadêmico para prática de desenvolvimento web com PHP, banco de dados e autenticação de usuários.
