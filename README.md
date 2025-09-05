# Desafio Accenture – Testes de API

Este projeto contém testes automatizados de API usando **Postman** e **Newman**, com integração a **GitHub Actions** para execução contínua e geração de relatórios HTML e JUnit.

---

O Desafio resume-se ao fluxo abaixo:
1. Criar um usuário
2. Gerar um token de acesso
3. Confirmar se o usuário criado está autorizado
4. Listar os livros disponíveis
5. Alugar dois livros de livre escolha
6. Listar os detalhes do usuário com os livros escolhidos

---

## 🔧 Pré-requisitos

- [Node.js](https://nodejs.org/en/) >= 18  
- npm (vem com Node.js) 
- Postman (opcional, apenas para editar/exportar collection e environment)

Verifique a instalação:

node -v
npm -v

---
## 💻 Instalação das dependências

Instale Newman e o reporter HTML Extra globalmente:

npm install -g newman newman-reporter-htmlextra

---
🚀 Executando os testes localmente
mkdir -p reports
newman run tests/postman/DesafioAccentureAPI.postman_collection.json \
  -e tests/postman/DesafioAccentureEnv.postman_environment.json \
  -r cli,htmlextra \
  --reporter-htmlextra-export reports/newman-report.html

O comando acima irá:
- Executar toda a collection
- Gerar um relatório HTML em reports/newman-report.html

---
🏗️ Integração CI/CD (GitHub Actions)

Workflow: .github/workflows/api-tests.yml

Aciona em:

Push para main

Pull Requests

Execução manual (workflow_dispatch)

Gera relatórios:

newman-report.html (HTML bonito)

junit.xml (padrão JUnit)

Injeta variáveis e segredos do GitHub Actions (Repository Secrets e Variables).

---
🔑 Variáveis e Secrets
Secrets (sensíveis):

API_USER – Usuário da API

API_PASSWORD – Senha da API

API_TOKEN – Token de autenticação

Variables (não sensíveis):

BASE_URL – URL base da API (ex.: https://demoqa.com)

Usados pelo Newman via --env-var para substituir placeholders da collection.

---
📝 Adicionando novos testes

Abra a collection no Postman e adicione requests ou scripts.

Exporte novamente para JSON

Commit e push; o workflow no GitHub Actions rodará automaticamente.

---
📊 Visualização dos relatórios

Localmente: abra reports/newman-report.html no navegador.

No GitHub Actions: Actions → Workflow run → Artifacts → postman-reports → baixe newman-report.html.
