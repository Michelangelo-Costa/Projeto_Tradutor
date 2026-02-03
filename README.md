# Projeto Tradutor 🈳🌍

[![Status](https://img.shields.io/badge/status-completo-green)](https://github.com/) [![Linguagens](https://img.shields.io/badge/lang-HTML%20%7C%20CSS%20%7C%20JS-blue)](https://github.com/)

Resumo
------
Pequeno tradutor front-end que utiliza a API pública MyMemory para traduzir texto. A interface oferece:

- Área de texto para entrada
- Seletor de idioma alvo
- Botão para traduzir
- Botão de microfone para entrada por voz (reconhecimento em navegadores compatíveis)

Demonstração
-----------
Abra `index.html` em um servidor local (recomendado) e teste a tradução e o reconhecimento de voz.

Tecnologias
-----------
- HTML, CSS e JavaScript puro
- API: `https://api.mymemory.translated.net`

Como executar (local)
---------------------
> É recomendado usar um servidor local (HTTPS ou `localhost`) para evitar bloqueios do `fetch`.

- VS Code: instale a extensão **Live Server** e clique em **Go Live**.
- Python 3 (PowerShell / Terminal):

```powershell
cd c:\Users\miche\Downloads\Projeto_Tradutor
python -m http.server 8000
# Abra: http://localhost:8000
```

- Node (http-server):

```bash
npm install -g http-server
http-server -c-1
```

Uso
---
1. Digite o texto em português na caixa principal.
2. Selecione o idioma alvo no seletor (`.idioma`).
3. Clique em **Traduzir** para obter o resultado.
4. Clique no botão de microfone para usar reconhecimento de voz (quando suportado).

Notas sobre reconhecimento de voz (microfone)
---------------------------------------------
- A API de reconhecimento de fala (`SpeechRecognition` / `webkitSpeechRecognition`) funciona melhor no **Chrome/Edge**.
- O recurso normalmente exige **HTTPS** ou **localhost** e permissão do usuário para acessar o microfone.
- Se o navegador não suportar reconhecimento de voz, o botão tem um fallback: usa síntese de voz para **ler** a tradução.

Como alterar o idioma alvo (exemplo)
------------------------------------
O `scripts.js` monta a URL de tradução. Para usar o idioma selecionado no `<select class="idioma">`:

```javascript
const seletor = document.querySelector('.idioma');
const idiomaDestino = seletor.value; // ex.: 'en', 'es', 'fr'
const endereco = `https://api.mymemory.translated.net/get?q=${encodeURIComponent(inputTexto.value)}&langpair=pt-BR|${idiomaDestino}`;
```

Melhorias e ideias para PRs
---------------------------
- Detectar automaticamente o idioma de origem
- Mapear nomes do idioma para códigos de idioma legíveis na UI
- Adicionar indicador visual durante o reconhecimento (ex.: ícone "ouvindo")
- Adicionar testes e CI

Controle de versão (git)
------------------------
```bash
git add .
git commit -m "Descrição das mudanças"
git push
```

Contribuição
------------
PRs são bem-vindas! Para contribuir:
1. Fork o repositório
2. Crie uma branch com a feature: `git checkout -b feature/minha-feat`
3. Faça commits com mensagens descritivas
4. Abra um Pull Request

Licença
-------
MIT — sinta-se livre para usar, alterar e distribuir.

Contato
-------
Se quiser que eu implemente alguma melhoria (ex.: toggle de microfone, indicador visual, ou suporte a mais idiomas), abra uma issue ou PR — ou me diga aqui que eu aplico as mudanças.

