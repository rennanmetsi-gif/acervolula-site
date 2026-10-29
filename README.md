# Publicação do Acervo Lula

Este repositório contém **somente a automação de publicação** em [acervolula.com.br](https://acervolula.com.br/). A fonte única das páginas é [`rennanmetsi-gif/data2commsfinal`](https://github.com/rennanmetsi-gif/data2commsfinal), branch `main`.

## Leia antes de trabalhar

O [guia completo de manutenção, particularidades e cuidados está no README da fonte](https://github.com/rennanmetsi-gif/data2commsfinal/blob/main/README.md). Ele documenta agenda, formulário/Apps Script, curadoria, GA4, notificações, SEO e convivência com a Data2Comms. Edite páginas e mantenha esse guia **na fonte**, não neste repositório.

## Como funciona

O workflow [Publicar Acervo Lula](.github/workflows/acervolula-pages-deploy.yml):

1. Baixa `data2commsfinal/main`.
2. Substitui o CNAME do checkout de build por `acervolula.com.br` e define a página do Acervo na raiz (`index.html`).
3. Compila com Ruby 3.2 e `bundle exec jekyll build`.
4. Gera robots/sitemap específicos do Acervo e aplica `noindex,follow` aos HTMLs fora da raiz.
5. Publica `_site` no GitHub Pages.

Dispara por push neste `main`, execução manual (`workflow_dispatch`) ou agendamento `*/5 * * * *`. O cron pode atrasar; não há garantia de atualização imediata. Para publicar uma mudança da fonte agora, use **Actions → Publicar Acervo Lula → Run workflow** e acompanhe o resultado. Não é necessário editar este README nem criar commit vazio para disparar manualmente.

## Cuidados

- Não copie HTML, agenda ou assets para cá: seriam ignorados pelo checkout da fonte e criariam duas versões confusas.
- Não mude o CNAME ou a URL global de `data2commsfinal` para o domínio Acervo; a mesma fonte publica a agência.
- Não confunda hash deste repositório com a versão de conteúdo compilada: confira o checkout da fonte no log do workflow.
- Push aceito não comprova deploy; confira Actions e a alteração efetiva no domínio público.
- A configuração SEO deste workflow pertence ao Acervo. Não a aplique indiscriminadamente ao domínio institucional.
- Não exponha credenciais no workflow, README ou logs.

Revisado em **17/10/2026**. O detalhamento funcional é mantido somente no README da fonte para evitar divergência entre documentos.
