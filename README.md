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
📊 Visualização dos relatórios

Localmente: abra newman-report.html no navegador.
