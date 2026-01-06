# FutPlus — Site estático

Resumo rápido
- Site estático com HTML, CSS e JavaScript vanilla.
- Mudanças recentes: padronização visual (CSS), namespace `window.FutPlus` para JS, páginas narrativas para categorias.

Pré-requisitos locais
- Navegador moderno (Chrome/Edge/Firefox)
- Git (opcional)
- Node/Python apenas se quiser servir localmente com servidor simples

Servir localmente (recomendado)
- Usando Python 3:

```bash
cd /workspaces/FutPlus
python3 -m http.server 8000
# Abra http://localhost:8000
```

- Usando Node (serve):

```bash
npm install -g serve
serve -s . -l 8000
# Abra http://localhost:8000
```

Checklist rápido de QA antes de publicar
- UI / Visual
  - [ ] Hero: vídeo/poster carregando corretamente em `index.html` e em `brasileirao.html`, `europeus.html`, `retro.html`.
  - [ ] Badges (`.badge-discount`, `.promo-badge`) não encavalam o conteúdo em resoluções grandes e pequenas.
  - [ ] Botões usam o estilo padronizado (`--accent`, `--btn-padding`).
  - [ ] Inputs e formulários exibem estado de foco com `--accent`.

- Funcional
  - [ ] Adicionar ao carrinho (qualquer produto) atualiza `#cart-count`.
  - [ ] Aplicar cupom (`FUT10`, `COMBO2`, `COMBO3`) funciona conforme regras.
  - [ ] Calcular frete com CEP (via ViaCEP) preenche `#shipping-result` / `#frete-val` e atualiza totais.
  - [ ] Checkout abre WhatsApp com resumo do pedido.
  - [ ] Contato: envio por EmailJS (se `window.EMAILJS_USER_ID` configurado) ou fallback `mailto`.

Observações importantes
- Vídeos: os arquivos referenciados em `img_roles/*.mp4` são opcionais. Se não estiverem presentes, o browser mostrará o `poster` do vídeo.
- EmailJS: verifique o Public Key em `contact.js` / `contact.html` se quiser testar envio via EmailJS.
- Frete: `JS/cep.js` usa ViaCEP e possui fallback local. A flag `window.FORCE_LOCAL_FRETE = true` força cálculo local.

Publicação no GitHub Pages (opcional)
- Simples (branch `main`): vá em Settings → Pages e escolha `main`/`/ (root)` como fonte.
- Ou usar `gh-pages` branch:

```bash
# instalar gh-pages (se usar Node app pipeline)
# git checkout -b gh-pages
# git push origin gh-pages
```

Comandos Git úteis (já executei commit + push):
```bash
git status
git add .
git commit -m "mensagem"
git push origin main
```

Próximos passos sugeridos
- Reunir os clipes de vídeo finais e substituir os arquivos `img_roles/*_loop.mp4` e `*_clip.mp4` por conteúdos otimizados (WebM + MP4). Prefira WebM para melhor compressão.
- Fazer testes manuais nos fluxos de compra em desktop e mobile.
- Gerar relatório de sugestões e correções prioritárias (posso gerar automaticamente se quiser).

Se quiser, eu:
- adiciono o README no repositório (já incluído aqui);
- gero um checklist mais detalhado para QA automatizado;
- substituo os posters/vídeos se você enviar os arquivos.

Desenvolvido como apoio para revisão e deploy — me diga qual próximo passo prefere.