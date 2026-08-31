# Sabrina Ferreira Interiores

Site institucional de página única. HTML, CSS e JavaScript puros, sem dependências
e sem etapa de build: basta servir a pasta.

## Rodar localmente

```sh
python3 -m http.server 8899
```

Abra <http://localhost:8899>.

## Estrutura

| Arquivo | Conteúdo |
|---|---|
| `index.html` | Todas as seções da página |
| `styles.css` | Estilos e paleta (variáveis CSS no `:root`) |
| `projetos.js` | Catálogo dos projetos que monta a grade e as galerias |
| `script.js` | Menu mobile, filtro, lightbox, tira da CASACOR e envio do formulário |
| `assets/hero/` | Banner do primeiro bloco (desktop e mobile) |
| `assets/projetos/<slug>/` | Capa e fotos de cada projeto, já redimensionadas |
| `assets/sabrina.webp`, `assets/equipe.webp` | Retrato da arquiteta e foto do time |
| `assets/marca.svg` | Símbolo usado como favicon |
| `originais/` | Fotos originais enviadas pelo cliente. **Não publicar** (1,4 GB) |

Todas as imagens são WebP, com uma exceção deliberada: `assets/hero/banner.jpg`
existe só para servir de `og:image`. WhatsApp e Facebook não leem WebP de forma
confiável no preview de link, então essa tag aponta para o JPEG. Não apague.

O site publicado tem cerca de 23 MB. A pasta `originais/` fica de fora do deploy;
ela existe só para reprocessar as imagens quando for preciso.

## Publicar um projeto novo

1. Crie `assets/projetos/<slug>/` com `cover.webp` (1100×825) e as fotos
   numeradas `01.webp`, `02.webp`, … (lado maior de 1600 px, WebP qualidade 80).
2. Some uma entrada em `projetos.js` com `slug`, `nome`, `cat`, `rotulo`,
   `nota`, `alt` e `fotos` (a quantidade de arquivos numerados).
3. `cat` precisa bater com um dos botões de filtro do `index.html`:
   `residencial`, `comercial`, `hotelaria` ou `casacor`.

Duas peças da grade são largas (`largo: true`): a primeira e a sétima. Com 13
projetos isso fecha cinco linhas cheias em três colunas. Se o número de projetos
mudar, reveja quais entradas levam `largo`.

## Ainda a preencher

- **Logo oficial** — não veio arquivo da marca. O cabeçalho e o rodapé usam um
  lockup tipográfico ("Sabrina Ferreira / Interiores") com um símbolo em arco.
  Assim que houver o PNG/SVG da marca, é só trocar o `<svg class="marca__icone">`
  no `index.html` por um `<img>` e ajustar `.marca__icone` no CSS.
- **Registro CAU** — o rodapé hoje traz só o nome; se quiser exibir o número,
  ele entra em `.rodape__legal`.
- **Analytics** — o GTM e o Microsoft Clarity do site anterior foram removidos
  (as contas eram de outro cliente). Para medir acessos, inclua os códigos
  próprios da Sabrina no `<head>`.
- **Domínio** — a tag `<link rel="canonical">` aponta para
  `https://www.sabrinaferreirainteriores.com/`; confirme o endereço final.
- **Search Console** — instalar no dia do deploy. É a única fonte que mostra as
  buscas reais que trazem gente ao site, inclusive as que as ferramentas de
  volume marcam como zero.
- **Dados estruturados** — ainda não há JSON-LD de `LocalBusiness`. Para incluir
  faltam horário de atendimento e coordenadas do escritório.

## Formulário de contato

Não envia e-mail. Ele monta a mensagem e abre o WhatsApp com o texto pronto,
por isso não exige servidor. Para receber por e-mail, seria preciso plugar um
serviço externo.

O WhatsApp está configurado como `5548988482359`, definido em `script.js` e nos
links do `index.html`.
