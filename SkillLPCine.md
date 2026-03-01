---
name: lp-cine-verde
description: >
  Constrói landing pages de alta conversão no estilo "cine verde" — paleta verde-escuro + branco + cinza,
  grid de cards com sombra sutil, seções intercaladas claras/escuras, hero com imagem de produto/pessoa,
  seção de pricing em 4 colunas com destaque central, FAQ accordion e formulário final.
  Use quando o usuário pedir uma landing page de produto físico, suplemento, curso ou serviço de saúde/bem-estar.
---

# Skill: LP Cine Verde

Esta skill define os padrões visuais, estrutura de seções, tipografia, componentes e código base
para construir landing pages de alta conversão no estilo "cine verde" — inspirado em páginas de
produtos de saúde, bem-estar e serviços premium com fundo branco/cinza claro, detalhes em verde
e cartões com sombra elegante.

---

## 1. Paleta de Cores

| Token              | Valor        | Uso                                              |
|--------------------|--------------|--------------------------------------------------|
| `--green-primary`  | `#3D8B37`    | Botões CTA, ícones de check, bordas de destaque  |
| `--green-dark`     | `#2E7D32`    | Hero fundo escuro, seções alternadas verdes      |
| `--green-light`    | `#E8F5E9`    | Fundo de seções alternadas claras                |
| `--green-mid`      | `#4CAF50`    | Hover de botões, badges de destaque              |
| `--gray-text`      | `#4A5568`    | Texto de parágrafos e legendas                   |
| `--gray-dark`      | `#2D2D2D`    | Títulos H1/H2 em fundo branco                    |
| `--gray-bg`        | `#F7F7F7`    | Fundo de seções alternadas neutras               |
| `--white`          | `#FFFFFF`    | Fundo principal, texto em seções escuras         |
| `--shadow-card`    | `0 4px 18px rgba(0,0,0,.10)` | Sombra padrão para cards  |
| `--shadow-hover`   | `0 8px 32px rgba(0,0,0,.18)` | Sombra no hover dos cards |

### Tokens CSS base:
```css
:root {
  --green-primary: #3D8B37;
  --green-dark:    #2E7D32;
  --green-light:   #E8F5E9;
  --green-mid:     #4CAF50;
  --gray-text:     #4A5568;
  --gray-dark:     #2D2D2D;
  --gray-bg:       #F7F7F7;
  --white:         #FFFFFF;
  --radius-sm:     8px;
  --radius-md:     16px;
  --radius-lg:     24px;
  --shadow-card:   0 4px 18px rgba(0,0,0,.10);
  --shadow-hover:  0 8px 32px rgba(0,0,0,.18);
  --transition:    all .25s ease;
}
```

---

## 2. Tipografia

| Elemento         | Família         | Peso | Tamanho             |
|------------------|-----------------|------|---------------------|
| Hero H1          | `Montserrat`    | 900  | clamp(2.2rem, 6vw, 3.4rem) |
| H2 Seções        | `Montserrat`    | 800  | clamp(1.6rem, 4vw, 2.4rem) |
| H3 Cards         | `Montserrat`    | 700  | 1.05rem             |
| Corpo / parágrafos | `Inter`       | 400  | 1rem – 1.05rem, line-height 1.7 |
| Labels / eyebrows  | `Inter`       | 700  | 0.78rem, UPPERCASE, letter-spacing 0.1em |
| Preços            | `Montserrat`   | 900  | 2rem+               |

### Import Google Fonts:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700;800;900&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---

## 3. Estrutura de Seções (Obrigatória)

Sempre construir nesta ordem:

```
1. NAVBAR          → logo + CTA verde fixo no topo
2. HERO            → imagem de produto/pessoa + H1 + benefício + CTA verde
3. RAZÕES          → "Por que escolher..." — grid 3×2 de cards brancos com ícone circular verde
4. DEPOIMENTO      → citação em destaque + foto + nome + estrelas (fundo cinza claro)
5. BENEFÍCIOS      → seção fundo verde com grid 3×3 de itens com ícone branco + texto branco
6. PROVA SOCIAL    → imagem lateral + texto + lista de resultados com ✔️ verde
7. PRICING         → 4 cards de planos, card central destacado em verde, com botão CTA
8. ATENDIMENTO     → fundo verde escuro, foto de atendente + CTA para WhatsApp/formulário
9. FAQ             → accordion com 5–7 perguntas, fundo branco
10. CTA FINAL      → fundo verde + formulário simples (nome, tel, email) + botão grande
11. FOOTER         → fundo verde-escuro, links + selos de segurança
```

---

## 4. Componentes Padrão

### 4.1 NAVBAR
- Fundo verde-escuro (`var(--green-dark)`) quando no topo
- Ao fazer scroll: fundo branco com `box-shadow`
- Logo: texto branco + ícone/leaf SVG à esquerda
- CTA: botão verde claro com texto escuro, borda-radius 50px
- Sem links de menu visíveis — foco total na conversão

```css
.navbar {
  position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
  background: var(--green-dark);
  padding: 14px 0;
  transition: var(--transition);
}
.navbar.scrolled {
  background: var(--white);
  box-shadow: 0 2px 16px rgba(0,0,0,.12);
}
.navbar__logo-text { color: var(--white); font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 1.4rem; }
.navbar.scrolled .navbar__logo-text { color: var(--green-dark); }

.btn-cta {
  background: var(--green-primary);
  color: var(--white);
  padding: 12px 28px;
  border-radius: 50px;
  font-weight: 700;
  font-size: .9rem;
  border: none;
  cursor: pointer;
  transition: var(--transition);
}
.btn-cta:hover { background: var(--green-mid); transform: translateY(-2px); }
```

---

### 4.2 HERO
- Layout: duas colunas (60% texto / 40% imagem produto) em desktop; coluna única em mobile
- Fundo: gradiente verde-escuro para verde-médio, com partículas/folhas opacas decorativas
- Badge: pílula glassmorphism com texto ("✅ Produto X – Fórmula Exclusiva")
- H1: máx 10 palavras, negrito, cor branca
- Subtítulo: 1–2 linhas, rgba(255,255,255,.85)
- CTA principal: botão verde claro grande, ícone WhatsApp opcional
- Stats abaixo: 3 números em linha (ex: "5.000+ clientes", "98% satisfação", "Envio em 24h")

```css
.hero {
  background: linear-gradient(135deg, var(--green-dark) 0%, var(--green-primary) 100%);
  min-height: 100svh;
  display: flex; align-items: center;
  padding: 120px 0 80px;
  position: relative; overflow: hidden;
}
.hero__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
  align-items: center;
}
@media (max-width: 768px) { .hero__grid { grid-template-columns: 1fr; } }
.hero__img { border-radius: var(--radius-lg); box-shadow: 0 20px 60px rgba(0,0,0,.3); }
```

---

### 4.3 RAZÕES ("Por que escolher...")
- Fundo: branco
- Label (eyebrow): verde, uppercase, pequeno
- H2: cinza-escuro, centralizado
- Grid: 3 colunas × 2 linhas de cards (em mobile: 1 coluna)
- Card: fundo branco, borda 1px cinza-100, border-radius 16px, sombra, hover eleva
- Ícone: círculo verde com SVG/emoji branco dentro (48px)
- Título: 1 linha, Montserrat 700
- Texto: 2–3 linhas, Inter 400, cinza

```css
.razoes__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  margin-top: 48px;
}
@media (max-width: 900px) { .razoes__grid { grid-template-columns: 1fr 1fr; } }
@media (max-width: 550px) { .razoes__grid { grid-template-columns: 1fr; } }

.razao-card {
  background: var(--white);
  border: 1px solid #E2E8F0;
  border-radius: var(--radius-md);
  padding: 32px 24px;
  box-shadow: var(--shadow-card);
  transition: var(--transition);
}
.razao-card:hover { box-shadow: var(--shadow-hover); transform: translateY(-6px); }

.razao-card__icon {
  width: 52px; height: 52px;
  background: var(--green-primary);
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 1.5rem;
  margin-bottom: 18px;
}
.razao-card__title { font-family: 'Montserrat', sans-serif; font-weight: 700; font-size: 1rem; color: var(--gray-dark); margin-bottom: 10px; }
.razao-card__text { font-size: .9rem; color: var(--gray-text); line-height: 1.65; }
```

---

### 4.4 DEPOIMENTO / PROVA SOCIAL
- Fundo: `var(--gray-bg)` (cinza muito claro)
- Layout centralizado, máx-width 700px
- Citação: itálico, fonte grande (1.25rem), cinza-escuro
- Foto: círculo 72px com borda verde
- Nome + papel: negrito + cor cinza, menores
- Estrelas: ★★★★★ em verde

```css
.depoimento {
  background: var(--gray-bg);
  padding: 72px 0;
  text-align: center;
}
.depoimento__quote {
  font-size: clamp(1.1rem, 2.5vw, 1.3rem);
  font-style: italic;
  color: var(--gray-dark);
  max-width: 680px; margin: 0 auto 28px;
  line-height: 1.7;
}
.depoimento__avatar {
  width: 72px; height: 72px; border-radius: 50%;
  border: 3px solid var(--green-primary);
  object-fit: cover; margin: 0 auto 12px;
}
.depoimento__stars { color: var(--green-primary); font-size: 1.2rem; margin-bottom: 8px; }
```

---

### 4.5 BENEFÍCIOS (Fundo Verde)
- Fundo: `var(--green-primary)` ou gradiente verde
- Todos os textos: branco
- Grid: 3 colunas × 3 linhas (desktop), 1 col (mobile)
- Cada item: ícone branco 28px + título branco 700 + texto rgba(255,255,255,.85)
- Sem cards com borda — itens "flutuam" no fundo verde

```css
.beneficios {
  background: linear-gradient(135deg, var(--green-dark) 0%, var(--green-primary) 100%);
  padding: 72px 0;
  color: var(--white);
}
.beneficios__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 36px 48px;
  margin-top: 48px;
}
@media (max-width: 768px) { .beneficios__grid { grid-template-columns: 1fr; } }

.beneficio-item { display: flex; gap: 16px; align-items: flex-start; }
.beneficio-item__icon { font-size: 1.6rem; flex-shrink: 0; margin-top: 2px; }
.beneficio-item__title { font-family: 'Montserrat', sans-serif; font-weight: 700; font-size: 1rem; margin-bottom: 6px; }
.beneficio-item__text { font-size: .9rem; color: rgba(255,255,255,.85); line-height: 1.6; }
```

---

### 4.6 PROVA SOCIAL COM IMAGEM LATERAL
- Layout: 50% imagem (arredondada, sombra) / 50% texto
- Lista de resultados: ✔ (verde) + texto com bold na parte principal
- Botão CTA opcional

```css
.prova__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: center;
}
@media (max-width: 768px) { .prova__grid { grid-template-columns: 1fr; } }
.prova__img { border-radius: var(--radius-lg); box-shadow: var(--shadow-hover); }
.prova__check-item { display: flex; gap: 12px; align-items: flex-start; margin-bottom: 16px; font-size: 1rem; color: var(--gray-dark); }
.prova__check-item::before { content: "✔"; color: var(--green-primary); font-weight: 700; flex-shrink: 0; }
```

---

### 4.7 PRICING (4 Cards de Planos)
- Fundo: `var(--gray-bg)`
- 4 cards em linha; card do meio (ou 2º/3º) com destaque:
  - borda `var(--green-primary)` 2px
  - badge "MAIS POPULAR" acima, fundo verde, texto branco
  - sombra maior
- Cada card: nome do plano, preço grande, período, lista de inclusões, botão CTA
- Botão nos cards normais: outline verde; botão no destacado: filled verde

```css
.pricing__grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  margin-top: 48px;
  align-items: start;
}
@media (max-width: 1024px) { .pricing__grid { grid-template-columns: 1fr 1fr; } }
@media (max-width: 600px) { .pricing__grid { grid-template-columns: 1fr; } }

.plan-card {
  background: var(--white);
  border-radius: var(--radius-md);
  padding: 32px 24px;
  box-shadow: var(--shadow-card);
  border: 1.5px solid #E2E8F0;
  position: relative;
}
.plan-card--featured {
  border-color: var(--green-primary);
  box-shadow: 0 12px 40px rgba(61,139,55,.25);
  transform: scale(1.04);
}
.plan-card__badge {
  position: absolute; top: -14px; left: 50%; transform: translateX(-50%);
  background: var(--green-primary); color: var(--white);
  padding: 4px 16px; border-radius: 50px; font-size: .75rem; font-weight: 700;
  white-space: nowrap;
}
.plan-card__name { font-family: 'Montserrat', sans-serif; font-weight: 700; font-size: 1rem; color: var(--gray-text); margin-bottom: 8px; }
.plan-card__price { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 2.4rem; color: var(--gray-dark); }
.plan-card__period { font-size: .8rem; color: var(--gray-text); margin-bottom: 20px; }
.plan-card__feature { display: flex; gap: 10px; align-items: flex-start; font-size: .88rem; color: var(--gray-text); margin-bottom: 10px; }
.plan-card__feature::before { content: "✔"; color: var(--green-primary); font-weight: 700; flex-shrink: 0; }
```

---

### 4.8 ATENDIMENTO (CTA com Atendente)
- Fundo: verde-escuro ou gradiente verde
- Layout: foto de pessoa (atendente/especialista) à esquerda + texto à direita
- Texto: branco
- Botão: branco com texto verde ou verde claro
- Opcional: produto(s) exibido(s) abaixo junto com selos de garantia

```css
.atendimento {
  background: var(--green-dark);
  padding: 72px 0;
  color: var(--white);
}
.atendimento__grid {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 48px;
  align-items: center;
}
@media (max-width: 768px) { .atendimento__grid { grid-template-columns: 1fr; text-align: center; } }
.atendimento__img {
  width: 220px; height: 280px; object-fit: cover;
  border-radius: var(--radius-lg);
  box-shadow: 0 20px 50px rgba(0,0,0,.3);
}
.btn-cta--white {
  background: var(--white);
  color: var(--green-dark);
  padding: 14px 32px;
  border-radius: 50px;
  font-weight: 700;
  font-size: 1rem;
  border: none;
  cursor: pointer;
  transition: var(--transition);
}
.btn-cta--white:hover { background: var(--green-light); }
```

---

### 4.9 FAQ (Accordion)
- Fundo: branco
- Cada item: borda-bottom `1px solid #E2E8F0`, padding vertical 20px
- Pergunta: Montserrat 700, cinza-escuro, cursor pointer, com ícone `+`/`−` verde à direita
- Resposta: Inter 400, cinza-médio, padding-top 12px
- Animação de abrir/fechar com `max-height` CSS ou JS simples

```css
.faq__item { border-bottom: 1px solid #E2E8F0; }
.faq__question {
  display: flex; justify-content: space-between; align-items: center;
  padding: 20px 0; cursor: pointer;
  font-family: 'Montserrat', sans-serif; font-weight: 700; font-size: 1rem; color: var(--gray-dark);
}
.faq__icon { color: var(--green-primary); font-size: 1.4rem; font-weight: 300; transition: transform .25s; }
.faq__item.open .faq__icon { transform: rotate(45deg); }
.faq__answer {
  max-height: 0; overflow: hidden; transition: max-height .35s ease, padding .25s;
  font-size: .93rem; color: var(--gray-text); line-height: 1.7;
}
.faq__item.open .faq__answer { max-height: 300px; padding-bottom: 20px; }
```

---

### 4.10 CTA FINAL
- Fundo: verde-escuro com padrão sutil de folhas/bolinhas (SVG inline ou `background-image`)
- Headline: branco, grande, centralizado (máx 12 palavras)
- Subtítulo: rgba(255,255,255,.82)
- Formulário simples: nome + telefone + email (campos com fundo branco, borda-radius 8px)
- Botão: verde claro grande (ou branco com texto verde)
- Micro-copy abaixo do botão: "🔒 Seus dados estão seguros. Sem spam."

```css
.cta-final {
  background: linear-gradient(135deg, var(--green-dark) 0%, var(--green-primary) 100%);
  padding: 80px 0;
  text-align: center;
  color: var(--white);
}
.cta-final__form {
  display: flex; flex-direction: column; gap: 14px;
  max-width: 420px; margin: 36px auto 0;
}
.cta-final__input {
  padding: 14px 18px;
  border: none; border-radius: var(--radius-sm);
  font-size: 1rem; font-family: 'Inter', sans-serif;
  outline: none;
}
.cta-final__input:focus { box-shadow: 0 0 0 3px rgba(76,175,80,.4); }
.cta-final__privacy { font-size: .8rem; color: rgba(255,255,255,.7); margin-top: 10px; }
```

---

### 4.11 FOOTER
- Fundo: `#1B5E20` (verde bem escuro)
- Logo branco + texto de copyright cinza-claro
- Links: Política de Privacidade · Termos · Contato (cinza claro, hover branco)
- Linha inferior: selos de segurança (SSL, pagamento seguro) alinhados ao centro ou direita

```css
footer {
  background: #1B5E20;
  color: rgba(255,255,255,.6);
  padding: 32px 20px;
  font-size: .85rem;
  text-align: center;
}
footer a { color: rgba(255,255,255,.6); transition: color .2s; }
footer a:hover { color: var(--white); }
```

---

## 5. Animações & Interações

### GSAP (obrigatório nas seções de scroll)
```js
gsap.registerPlugin(ScrollTrigger);

// Hero reveal
gsap.timeline()
  .from('.hero__badge', { y: 20, opacity: 0, duration: 0.6 })
  .from('.hero__title', { y: 30, opacity: 0, duration: 0.8 }, '-=0.4')
  .from('.hero__sub',   { y: 20, opacity: 0, duration: 0.6 }, '-=0.5')
  .from('.hero__ctas > *', { y: 20, opacity: 0, stagger: 0.12, duration: 0.5 }, '-=0.4');

// Cards em scroll
gsap.utils.toArray('.razao-card, .beneficio-item, .plan-card').forEach((el, i) => {
  gsap.from(el, {
    scrollTrigger: { trigger: el, start: 'top 85%' },
    y: 40, opacity: 0, duration: 0.6, delay: i * 0.08, ease: 'power2.out'
  });
});
```

### VanillaTilt (cards 3D)
```js
VanillaTilt.init(document.querySelectorAll('.razao-card, .plan-card'), {
  max: 12, speed: 400, glare: true, 'max-glare': 0.15, perspective: 900
});
```

### FAQ Accordion
```js
document.querySelectorAll('.faq__question').forEach(btn => {
  btn.addEventListener('click', () => {
    const item = btn.parentElement;
    const isOpen = item.classList.contains('open');
    document.querySelectorAll('.faq__item').forEach(i => i.classList.remove('open'));
    if (!isOpen) item.classList.add('open');
  });
});
```

---

## 6. Responsividade — Breakpoints

| Breakpoint | Comportamento                                           |
|------------|---------------------------------------------------------|
| `< 550px`  | 1 coluna em todos os grids; botões full-width            |
| `550–900px`| 2 colunas em razões e pricing                           |
| `> 900px`  | Layout completo; Hero 2 colunas; Razões 3 cols          |
| `> 1200px` | Pricing 4 colunas; max-width 1200px no container        |

---

## 7. Dependências Externas

```html
<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700;800;900&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

<!-- GSAP + ScrollTrigger -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

<!-- VanillaTilt (efeito 3D nos cards) -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.8.1/vanilla-tilt.min.js"></script>

<!-- Swiper (carrossel de depoimentos, se necessário) -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css">
<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
```

---

## 8. Checklist de Qualidade (antes de entregar)

- [ ] Todos os textos são em português do Brasil
- [ ] Hero tem H1 único com valor claro em ≤ 10 palavras
- [ ] Botão CTA usa cor verde de alto contraste (AA WCAG)
- [ ] Todas as imagens têm `alt` descritivo
- [ ] Formulário tem `label` ou `placeholder` claro em cada campo
- [ ] FAQ tem ao menos 5 perguntas reais (sem placeholder "Lorem ipsum")
- [ ] Footer tem link de Política de Privacidade
- [ ] Página renderiza corretamente em mobile (375px) e desktop (1280px)
- [ ] GSAP hero animation dispara no carregamento; scroll animations ao entrar na viewport
- [ ] Nenhum "Lorem ipsum" ou conteúdo de exemplo no código entregue

---

## 9. Adaptação para BigClean

Quando aplicar esta Skill para a **BigClean – Higienização de Estofados**:

| Campo                | Valor BigClean                                                    |
|----------------------|-------------------------------------------------------------------|
| **Produto/Serviço**  | Higienização profissional de estofados, colchões, tapetes e carros |
| **CTA principal**    | WhatsApp: `https://wa.me/5591984028561`                           |
| **Razões (6 cards)** | Higiene Profunda · Remoção de Manchas · Eliminação de Odores · Restauração de Cor · Atendimento a Domicílio · Equipamentos de Alta Tecnologia |
| **Benefícios (Verde)** | 9 itens sobre saúde, conforto, praticidade, economia           |
| **Pricing**          | Sofá (1 lugar) · Sofá (2–3 lug.) · Colchão · Pacote Completo    |
| **Atendente**        | Foto do técnico/equipe BigClean com uniforme                      |
| **FAQ**              | Quanto tempo leva? · Precisa sair de casa? · Que produtos usam? · Quanto custa? · Como agendar? |
| **CTA Final**        | "Solicite seu Orçamento Gratuito" → formulário nome + telefone   |
| **Paleta**           | Trocar `--green-primary` por `#1565C0` (azul BigClean) se necessário, mantendo estrutura |

---

## 10. Exemplo de HTML Esqueleto Completo

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[Nome] – [Benefício Principal]</title>
  <!-- Fonts, GSAP, VanillaTilt, Swiper -->
  <style>/* tokens + componentes conforme seções 1–4 */</style>
</head>
<body>

  <!-- 1. NAVBAR -->
  <nav class="navbar" id="navbar">...</nav>

  <!-- 2. HERO -->
  <section class="hero" id="hero">
    <div class="container hero__grid">
      <div class="hero__content">
        <div class="hero__badge">✅ Badge de confiança</div>
        <h1 class="hero__title">Título poderoso aqui</h1>
        <p class="hero__sub">Subtítulo com benefício claro.</p>
        <a class="btn-cta" href="#cta">Chamar no WhatsApp</a>
        <div class="hero__stats">
          <div><strong>5.000+</strong><span>clientes</span></div>
          <div><strong>98%</strong><span>satisfação</span></div>
          <div><strong>24h</strong><span>resposta</span></div>
        </div>
      </div>
      <img class="hero__img" src="imagem-produto.jpg" alt="Produto X">
    </div>
  </section>

  <!-- 3. RAZÕES -->
  <section class="section" id="razoes">
    <div class="container text-center">
      <span class="section__label">Por que nos escolher</span>
      <h2 class="section__title">6 Razões para Confiar em Nós</h2>
      <div class="razoes__grid">
        <!-- 6x .razao-card -->
      </div>
    </div>
  </section>

  <!-- 4. DEPOIMENTO -->
  <section class="depoimento" id="depoimento">...</section>

  <!-- 5. BENEFÍCIOS -->
  <section class="beneficios" id="beneficios">
    <div class="container text-center">
      <span class="section__label" style="color:rgba(255,255,255,.7)">Diferenciais</span>
      <h2 class="section__title">Benefícios do Serviço</h2>
      <div class="beneficios__grid">
        <!-- 9x .beneficio-item -->
      </div>
    </div>
  </section>

  <!-- 6. PROVA SOCIAL -->
  <section class="section" id="prova">
    <div class="container prova__grid">
      <img class="prova__img" src="foto-resultado.jpg" alt="Resultado">
      <div class="prova__texto">
        <h2>Veja os Resultados Reais</h2>
        <div class="prova__check-item">Benefício 1 aqui</div>
        <!-- mais itens -->
      </div>
    </div>
  </section>

  <!-- 7. PRICING -->
  <section class="section" id="planos" style="background:var(--gray-bg)">
    <div class="container text-center">
      <h2>Escolha seu Plano</h2>
      <div class="pricing__grid">
        <!-- 4x .plan-card, 1 com .plan-card--featured -->
      </div>
    </div>
  </section>

  <!-- 8. ATENDIMENTO -->
  <section class="atendimento" id="atendimento">...</section>

  <!-- 9. FAQ -->
  <section class="section" id="faq">
    <div class="container" style="max-width:780px">
      <h2 class="text-center section__title">Perguntas Frequentes</h2>
      <div class="faq__list">
        <!-- 5–7x .faq__item -->
      </div>
    </div>
  </section>

  <!-- 10. CTA FINAL -->
  <section class="cta-final" id="cta">
    <div class="container">
      <h2>Solicite seu Orçamento Gratuito</h2>
      <p>Atendimento rápido. Sem compromisso.</p>
      <form class="cta-final__form">
        <input class="cta-final__input" type="text" placeholder="Seu nome">
        <input class="cta-final__input" type="tel" placeholder="WhatsApp">
        <button class="btn-cta" type="submit">Quero meu Orçamento →</button>
        <p class="cta-final__privacy">🔒 Seus dados estão seguros. Sem spam.</p>
      </form>
    </div>
  </section>

  <!-- 11. FOOTER -->
  <footer>...</footer>

  <script>/* GSAP + VanillaTilt + FAQ accordion */</script>
</body>
</html>
```