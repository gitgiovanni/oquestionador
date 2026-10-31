# O Questionador 📚🤖

![Versão](https://img.shields.io/badge/version-1.0-blue.svg)
![Node.js](https://img.shields.io/badge/Node.js-Express-green.svg)
![MySQL](https://img.shields.io/badge/MySQL-Relational_DB-orange.svg)

**O Questionador** é uma Prova de Conceito (Proof of Concept - PoC) desenvolvida para demonstrar a viabilidade técnica da **Transparência Algorítmica** e da **Explicabilidade** em softwares educacionais (*Learning Analytics*). 

Este projeto foi construído como parte de uma pesquisa aplicada sobre as Aplicações Éticas da Inteligência Artificial na Educação, opondo-se à opacidade das "caixas-pretas" algorítmicas e respeitando rigorosamente a Lei Geral de Proteção de Dados Pessoais (LGPD).

## 🚀 Funcionalidades Principais

* **Algoritmo Transparente:** Sistema de recomendação baseado em regras determinísticas (*rule-based*). Em vez de ocultar a lógica de adaptação da trilha, o sistema exibe ao aluno a justificativa pedagógica exata para a seleção da próxima questão.
* **Dashboard de Desempenho:** Interface gráfica onde o aluno pode acompanhar sua taxa de aproveitamento geral e o domínio por tópicos específicos (Matemática, Português, História, Geografia, Inglês e Tecnologia).
* **Conformidade com a LGPD (Art. 14):** 
  * Cadastro exige consentimento expresso (focado em crianças/adolescentes).
  * Senhas armazenadas com criptografia *hash*.
  * Direito ao esquecimento: opção de exclusão definitiva (*hard delete*) da conta e de todo o histórico de respostas do banco de dados.
* **Banco de Questões:** Domínio de 48 questões baseadas na Base Nacional Comum Curricular (BNCC), divididas em níveis de dificuldade 1 e 2.

## 🛠️ Arquitetura e Tecnologias

O sistema utiliza uma arquitetura clássica de Cliente-Servidor:
* **Frontend:** HTML5, CSS3 (com design *glassmorphism*) e Vanilla JavaScript.
* **Backend:** Node.js com o microframework Express.
* **Banco de Dados:** MySQL (Relacional) para persistência segura de usuários, histórico de interações e métricas de desempenho.

## ⚙️ Instalação e Execução Local

Para rodar esta Prova de Conceito na sua máquina local, você precisará ter o Node.js e um servidor MySQL instalados.

### 1. Clonar o repositório
```bash
git clone https://github.com/gitgiovanni/oquestionador.git
cd oquestionador
```

### 2. Configurar o Banco de Dados
1. Abra o seu cliente MySQL (ex: MySQL Workbench).
2. Execute o script `database/schema.sql` (incluso no repositório) para criar as tabelas necessárias.
3. Popule o banco com as questões executando `database/seed.sql`.

### 3. Variáveis de Ambiente
Crie um arquivo `.env` na raiz do projeto e configure as credenciais do seu banco de dados:
```env
DB_HOST=localhost
DB_USER=seu_usuario
DB_PASS=sua_senha
DB_NAME=oquestionador_db
PORT=3000
```

### 4. Instalar dependências e Iniciar
```bash
npm install
npm start
```
O servidor estará rodando em http://localhost:3000.

## 📖 Como Usar (Testando a Explicabilidade)

1. Acesse a plataforma e realize um cadastro (simulando o consentimento).
2. Inicie a trilha de **Matemática (Álgebra)**.
3. **Cenário de Erro (Regra Ativa):** Erre intencionalmente uma questão de Nível 2.
4. Ao carregar a próxima pergunta (Nível 1), clique no botão **"Transparência Algorítmica"** no topo da questão.
5. O sistema justificará textualmente a regressão de dificuldade, provando o conceito de explicabilidade.

## 👥 Autores
Pesquisa e desenvolvimento conduzidos por:
* Giovanni Bordin Oséas
* Gabriel Rodrigues de Moura Pinto 
* Beatriz Gomes de Almeida
* Vitória dos Santos Marques Ferreira 
* Rebeca Lippi Gomes

*Sob a orientação do Prof. Nelson - Universidade São Judas Tadeu (USJT).*