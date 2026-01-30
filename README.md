# Projeto Tradutor 🈳🌍

**Descrição**

Pequeno tradutor front-end que usa a API pública MyMemory para traduzir texto do português para inglês. A interface contém uma área de texto para entrada, um seletor de idioma, um botão para traduzir e um botão de microfone (UI apenas).

---

## 🔧 Tecnologias

- HTML, CSS e JavaScript puro
- API usada: `https://api.mymemory.translated.net`

---

## ▶️ Como executar (local)

Recomendado: abrir o projeto em um servidor local (evita problemas com `fetch` em `file://`). Algumas opções:

- Usando o VS Code: instale a extensão **Live Server** e clique em "Go Live".

- Usando Python 3 (no PowerShell):
```powershell
# na pasta do projeto
python -m http.server 8000
# e abra: http://localhost:8000
```

- Usando Node (http-server):
```bash
npm install -g http-server
http-server -c-1
```

Ou simplesmente abra `index.html` no navegador, mas o `fetch` pode ser bloqueado dependendo do navegador/configuração.

---

## 🧭 Uso

1. Digite o texto em português na caixa principal.
2. Selecione o idioma (no momento o projeto usa tradução `pt-BR -> en` por padrão).
3. Clique em "traduzir" para ver o resultado na seção "Tradução".

---

## 🛠️ Como alterar o idioma (rápido)

Atualmente o código em `scripts.js` monta a URL com `"&langpair=pt-BR|en"` fixo. Para usar o valor do seletor (`<select class="idioma">`), substitua a linha que monta `endereco` por algo como:

```javascript
let seletor = document.querySelector('.idioma')
let idiomaDestino = seletor.value // Ex.: "en" ou "de" ou "ja"
let endereco = `https://api.mymemory.translated.net/get?q=${encodeURIComponent(inputTexto.value)}&langpair=pt-BR|${idiomaDestino}`
```

Assim você usa a opção selecionada para escolher o idioma alvo. (Se quiser, posso fazer essa alteração para você.)

---

## ✅ Controle de versão (Git)

Comandos básicos:

```powershell
# adicionar todas as mudanças
git add -A
# criar commit
git commit -m "Mensagem descritiva"
# enviar para o remoto
git push
```

---

## 🤝 Contribuição

PRs são bem-vindas! Algumas ideias:

- Suportar detecção automática de idioma de origem
- Mapear os nomes dos idiomas do `<select>` para códigos (ex.: "Inglês" -> `en`)
- Melhorar UI/UX e adicionar teste de integração
