# DESIGN.md · Site Marlizete Maldonado Vargas
**Versão:** 0.2 (26/10/2026) · substitui a paleta e o tema da v0.1 a partir das fotos que ela escolheu
**Status:** aguardando validação do Fran (e dela, antes de publicar)

---

## 1. Tema

**Conforto moderno.** É uma casa onde se trabalha com seriedade, não uma clínica. O site tem a temperatura do consultório (veludo terracota, tapete ocre, linho cru, palha, planta de verdade, luz de fim de tarde) e a estrutura limpa de um livro bem diagramado. Isso faz sentido porque ela é autora.

Duas faces, as duas presentes:
- **Autoridade:** 45 anos de clínica, doutorado, livro de referência. Aparece na tipografia serifada, no espaço em branco e na foto de preto e dourado.
- **Proximidade:** senta no chão, faz as próprias cartas, ri com o rosto inteiro. Aparece no linho quente, nas fotos sem pose e na moldura "de carta".

**O que o site não é:** não usa verde-sálvia de clínica, bege neutro de template, ícone de cérebro nem foto de banco.

**Pergunta que decide qualquer dúvida:** essa pessoa se reconhece aqui, ou estou pedindo que ela me reconheça?

---

## 2. Paleta

Contraste medido (WCAG) em 26/10/2026.

```css
:root {
  /* fundos */
  --linho:      #F5EEE3; /* fundo dominante, das mantas */
  --creme:      #FBF7F1; /* fundo alternado, cartões */
  --cafe:       #3A2A20; /* fundo escuro de seção, rodapé */

  /* texto */
  --tinta:      #3A2A20; /* texto principal: 11,9:1 sobre linho · 12,8:1 sobre creme */
  --tinta-2:    #6B5444; /* texto secundário: 6,1:1 sobre linho · 6,6:1 sobre creme */

  /* ação (uma por tela) */
  --terracota:  #A3472A; /* botão, link: 5,2:1 sobre linho; branco sobre ela 6,0:1 */

  /* calor e acento */
  --ocre:       #C99A3B; /* fios, numerais, detalhes. Como texto, só sobre café (5,3:1) */
  --vinho:      #7A2E33; /* acento raro: citação, marcador (8,0:1 sobre linho) */
  --folha:      #3F5A43; /* respiro raro: selo "online" (6,6:1 sobre linho) */
}
```

**Regras de cor**
- A terracota é a única cor de ação. Nada mais compete com ela na mesma tela.
- O ocre nunca vai como texto sobre fundo claro. Ele fica em fios, numerais grandes decorativos e bordas.
- O vinho e a folha aparecem, cada um, no máximo uma vez por seção.
- Fundo branco puro só dentro das molduras de foto.

---

## 3. Tipografia

| Papel | Fonte | Por quê |
|---|---|---|
| Títulos, citações | **Literata** (Google Fonts, eixo óptico) | É serifa de livro e combina com a autora. Calorosa sem ser rococó. Acentuação pt-BR completa. |
| Corpo, botões, navegação | **Atkinson Hyperlegible Next** (Google Fonts) | Legibilidade alta para público 40+, com personalidade suficiente para não parecer sistema. |

**Escala** (base 18px no desktop, 17px no celular)
- Display (hero): `clamp(2.4rem, 5vw, 3.6rem)`, Literata 500, altura de linha 1,1
- H2: `clamp(1.8rem, 3.2vw, 2.4rem)`, Literata 500
- H3: 1,3rem, Literata 600
- Corpo: 1rem, Atkinson 400, altura de linha 1,65, até 62 caracteres por linha
- Sobretítulo: 0,85rem, Atkinson 600, espaçamento 0,08em, caixa-alta só aqui (nunca em parágrafo)
- Legenda e rodapé: 0,9rem (mínimo 15px)

Itálico de Literata para citações e para o título do livro.

---

## 4. Motivo visual: a carta

As cartas de colagem que ela fez à mão são a assinatura do site. O que aproveitamos delas é o **formato**, não o conteúdo:

- **Moldura de carta:** foto em proporção 2:3, borda creme de 10px, sombra curta e quente (`0 2px 0 rgba(58,42,32,.08), 0 10px 24px -12px rgba(58,42,32,.35)`) e rotação estática de -1,5° ou 1,5°. Sem animação.
- **Usada com parcimônia:** no máximo duas por tela, e nunca em seções seguidas.
- **A foto de cima com as cartas espalhadas** entra uma vez, inteira, na seção "Como eu trabalho".

**Não fazer:** recortar uma carta isolada e usar como ilustração. As colagens usam imagens de terceiros (revistas, fotos), e ampliar uma delas sozinha vira reprodução dessas imagens. Também não redesenhamos as cartas em vetor.

---

## 5. Componentes

- **Botão primário:** fundo terracota, texto creme, Atkinson 600, padding 14×24, raio 999px (pílula macia), mínimo 48px de altura. Hover escurece para `#8A3B22` em 200ms.
- **Link de texto:** terracota, sublinhado de 1px com offset de 3px, que engrossa para 2px no hover.
- **Foco:** contorno de 3px em `--vinho`, com offset de 3px, em todo elemento interativo.
- **Cartão de atendimento:** fundo creme, borda superior de 3px em ocre, raio 6px, sem ícone grande. Abre com um numeral em Literata ocre (01, 02, 03) sobre fundo café, ou só com o título.
- **Citação:** Literata itálico 1,4rem, fio vertical de 3px em vinho à esquerda. Só frases que vieram dela, com fonte marcada.
- **Selo de modalidade:** "Presencial · Aracaju" e "Online · Brasil todo", com texto em `--tinta` e borda de 1px em folha ou ocre.
- **WhatsApp fixo:** botão pílula no canto, com rótulo de texto visível no desktop e ícone com `aria-label` no celular. Não pulsa.

---

## 6. Layout e ritmo

Container de 1120px, gutter de 20px no celular e 32px no desktop. Seções com 96px de respiro vertical no desktop e 64px no celular.

**Ordem proposta das seções** (o conteúdo depende da instrução de voz):

1. **Abertura:** foto da blusa rosa no consultório, à direita, em moldura de carta; nome, uma frase que diga quem ela atende e o botão do WhatsApp. Fundo linho.
2. **Para quem:** três frentes, na ordem de prioridade dela (casal e família presencial; famílias por adoção online; supervisão clínica). Cartões em fundo creme.
3. **O espaço:** foto larga da sala com o canto de almofadas, sangrando até a borda. Uma legenda curta. É respiro, quase sem texto.
4. **Como eu trabalho:** foto de cima com as cartas e texto ao lado. Fundo creme.
5. **Trajetória e livro:** foto de preto e dourado, linha do tempo enxuta (1981, 1991, 1998, 2000) com anos em ocre sobre fundo café. É a única seção escura no meio da página.
6. **Primeira conversa:** como agendar, presencial ou online, o que acontece no primeiro encontro. Perguntas frequentes em `<details>`.
7. **Contato e rodapé:** endereço, mapa estático ou link, CRP, CVV 188, SAMU 192 e LGPD.

**Ritmo:** linho → creme → foto sangrada → creme → café → linho → café. Nenhuma seção repete a anterior.

---

## 7. Profundidade

É plano com calor. A única sombra é a da moldura de carta. Não há glassmorphism, gradiente nem blob. Textura só nas fotos, e nada de textura de papel falsa em CSS.

---

## 8. Movimento (L1)

- Entrada por seção: opacidade 0→1 e deslocamento de 8px, em 400ms, uma vez, via IntersectionObserver.
- Transições de cor em 200ms.
- `prefers-reduced-motion: reduce` zera tudo.
- A rotação das cartas é estática e não conta como movimento.

---

## 9. Imagens: tratamento

| Foto | Uso | Tratamento necessário |
|---|---|---|
| Blusa rosa no consultório | Abertura | Recorte 2:3; nada a corrigir |
| Close de amarelo olhando para cima | Abertura no celular (alternativa) ou "Primeira conversa" | Recorte quadrado |
| Preta e dourado | Trajetória | Recorte 4:5 |
| De cima com as cartas | Como eu trabalho | Inteira, sem recortar cartas isoladas |
| P&B nas cartas | Uma vez, ou fora | É de outra linguagem; decidir |
| Sala ampla com almofadas | O espaço | Corrigir as verticais (grande-angular) |
| Poltronas e plantas | Reserva / "Para quem" | Corrigir as verticais |
| Sofá com janela | Reserva | Tirar o álcool em gel e a caixa de lenço do corte |
| Detalhe do sofá | Respiro pequeno | Não usar grande (marcas no veludo) |

Formato WebP com fallback JPG, `srcset` em 480/960/1600px, `loading="lazy"` exceto na foto de abertura, e `alt` descritivo em todas.

---

## 10. Fazer e não fazer

**Fazer**
- Usar as fotos reais dela e do espaço, sempre.
- Usar frase curta e categórica no fechamento de bloco, que é traço dela.
- Mostrar os anos como prova, sem adjetivo.
- Respeitar a proveniência: toda frase atribuída a ela precisa ter vindo dela.

**Não fazer**
- Inter, Roboto ou fonte de sistema; gradiente; blob; ícone grande decorativo.
- "Transforme sua vida", promessa de resultado, urgência, pop-up.
- "Especialista", depoimento, preço como chamariz, "antes e depois".
- Constelações familiares, em qualquer forma.
- Nomear o método das cartas no site antes da decisão dela (ver nota ética).
- Caso clínico, mesmo disfarçado.

---

## 11. Responsividade

Testar em 360, 768 e 1280px, sem rolagem horizontal. No celular, a foto de abertura vem antes do título e as molduras de carta perdem a rotação. Alvos de toque de no mínimo 44×44px. A navegação vira menu `<details>` acessível, sem JavaScript obrigatório.

---

## 12. Pendências que afetam o layout

- CRP (rodapé e JSON-LD): `[CRP: CONFIRMAR]`
- Número do endereço (465 ou 564), sala 403
- Como ela aparece: "Marlizete" com "Dra." onde o formato pedir (a confirmar)
- Se a foto P&B entra
- Se e como o trabalho com as cartas é nomeado

---

## 13. v0.3 (26/10/2026): mais corpo na diagramação

- **Abertura:** título editorial ("Casal, família *e adoção.*") com itálico terracota; arco terracota atrás de duas cartas sobrepostas (blusa rosa e close de amarelo).
- **Faixa de credenciais** em café, logo abaixo da abertura: 1981 · 1991 · 1998 · Doutora, com numerais em ocre.
- **Frentes em linhas alternadas:** casal com a foto das poltronas frente a frente; adoção com o quadro "Antes de entrar na fila" (três perguntas dela) no lugar de foto.
- **Faixa terracota** com uma única citação dela em Literata itálico grande.
- **Consultório em mosaico:** sala grande e detalhe do sofá, com o endereço (Clinical Center, Praça da Bandeira, 465, sala 403).
- **Espiral:** traço tirado do bordado das almofadas, usado no máximo duas vezes, sempre decorativo (`aria-hidden`).
- Supervisão clínica fora por enquanto. CRP 19/00613. "Dra." no título, no sobretítulo e no rodapé.

— rascunho: precisa de revisão humana antes de circular (HITL).
