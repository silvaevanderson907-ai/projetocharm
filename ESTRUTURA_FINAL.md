# Charm sucrè — Estrutura Final (HTML + CSS)

## 📋 Resumo do Projeto

Página de e-commerce para **Charm sucrè** — uma confeitaria gourmet com foco em layout responsivo, animações suaves e carrinho de compras.

---

## 🎨 Paleta de Cores

```css
:root{
  --bg:#fff7f6;              /* Fundo gradient */
  --surface:#ffffff;         /* Cards e superfícies */
  --muted:#6b6b6b;          /* Textos secundários */
  --accent-1:#d3548a;       /* Rosa principal */
  --accent-2:#ff7ba9;       /* Rosa claro */
  --accent-3:#ffcfdf;       /* Brilho / badges */
  --text:#22222a;           /* Texto principal */
  --shadow: 0 10px 30px rgba(16,16,16,0.08);
  --max-width:1120px;
}
```

---

## 📐 Layout Estrutura HTML

### Header Hero
```html
<header class="hero">
  <div class="container hero-inner">
    <div class="brand">
      <h1>Charm sucrè</h1>
      <p class="tag">Seu dia mais doce — sobremesas gourmets feitas com carinho</p>
    </div>
    <div class="header-ctas">
      <a class="btn ghost" href="#">Instagram</a>
      <a class="btn primary" href="#">Faça seu pedido</a>
    </div>
  </div>
</header>
```

### Main Layout (Grid 2 colunas)
```html
<main class="container layout">
  <!-- Coluna 1: Produtos -->
  <section class="produtos-area">
    <div class="section-header">
      <h2>Prateleiras de Sabores</h2>
      <p class="subtitle">Escolha seu sabor favorito...</p>
    </div>
    <div id="produtos"></div> <!-- Preenchido por head.js -->
  </section>

  <!-- Coluna 2: Carrinho Sticky -->
  <aside id="carrinho" class="cart">
    <div class="cart-inner">
      <h2>Seu Carrinho</h2>
      <ul id="lista-carrinho"></ul>
      <p id="total">Total: R$0,00</p>
      <div class="payment-methods">
        <h3>Pagamento</h3>
        <label><input type="radio" name="payment" value="pix"> Pix</label>
        <label><input type="radio" name="payment" value="cartao"> Cartão</label>
        <button onclick="finalizarCompra()" class="btn primary">Finalizar Compra</button>
      </div>
    </div>
  </aside>
</main>
```

---

## 🛍️ Estrutura do Card (gerada por head.js)

Cada produto é renderizado assim:

```html
<div class="card">
  <img src="./img/produto.jpg" alt="Nome Produto">
  <h3 class="title">Nome do Produto</h3>
  <p class="desc">Descrição (máx 2 linhas)</p>
  <div class="meta">
    <span class="price">R$ XX.XX</span>
  </div>
  <div class="actions">
    <button class="btn-add-cart" onclick="adicionarAoCarrinho(...)">
      Adicionar ao Carrinho
    </button>
  </div>
</div>
```

---

## 🎯 Classes CSS Principais

### Containers
| Classe | Descrição |
|--------|-----------|
| `.hero` | Header com gradiente rosa |
| `.container` | Max-width 1120px, auto margins |
| `.layout` | Grid 2 colunas: produtos + cart |
| `.shelf` | Prateleira com auto-fill grid |
| `.card` | Cartão do produto |

### Botões
| Classe | Descrição |
|--------|-----------|
| `.btn` | Base para todos os botões |
| `.btn.primary` | Rosa gradiente com shine animation |
| `.btn.ghost` | Transparente com borda branca |
| `.btn-add-cart` | Especial: gradiente + touch-pulse |

### Interatividades
```css
/* Prateleira no hover */
.shelf:hover {
  transform: translateY(-6px);
  box-shadow: 0 28px 60px rgba(16,16,16,0.06);
}

/* Cards elevam dentro da prateleira */
.shelf:hover .card {
  transform: translateY(-8px);
}

/* Imagem faz zoom */
.card:hover img {
  transform: scale(1.06);
}

/* Botão "Adicionar ao Carrinho" em clique */
.btn-add-cart:active {
  transform: scale(.96);
  animation: touch-pulse .4s ease;
}
```

### Animações Principais
| Nome | Efeito |
|------|--------|
| `float` | Hover flutuante em dispositivos touch |
| `shine` | Brilho deslizante no botão primary |
| `touch-pulse` | Pulse de sombra rosa ao clicar |

---

## 📱 Responsividade

```css
@media (max-width: 1080px) {
  .shelf { grid-template-columns: repeat(3, 1fr); }
}

@media (max-width: 880px) {
  .layout { grid-template-columns: 1fr; } /* Carrinho abaixo */
  .shelf { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 420px) {
  .shelf { grid-template-columns: 1fr; } /* 1 coluna */
}
```

---

## 🎬 Animações Detalhadas

### 1. Botão Primary (Hero)
- **Hover**: Eleva (-4px), gradiente desliza, box-shadow aumenta
- **Shine**: Brilho percorre o botão (.9s)
- **Focus**: Outline de 6px com cor accent

### 2. Botão "Adicionar ao Carrinho"
- **Hover**: Eleva (-3px), brilho +2%
- **Click**: Comprime (scale .96) + pulse de sombra rosa que expande

### 3. Prateleira Inteira
- **Hover**: Sobe (-6px), sombra + brilho
- **Cards filhos**: Sobem mais (-8px), imagens fazem zoom

### 4. Card Individual
- **Hover**: Eleva (-6px), sombra aumenta
- **Imagem**: Zoom suave (.6s cubic-bezier)

---

## 🔧 Variáveis CSS Recomendadas

Para customizar, edite `:root`:

```css
:root{
  --accent-1: #d3548a;      /* Cor principal (rosa) */
  --accent-2: #ff7ba9;      /* Destaque */
  --bg: #fff7f6;            /* Fundo */
  --max-width: 1120px;      /* Largura max */
  --shadow: 0 10px 30px rgba(16,16,16,0.08);
}
```

---

## ✅ Checklist de Implementação

- [x] Hero com gradiente e overlay
- [x] Grid responsivo (auto-fill)
- [x] Prateleiras com hover coletivo
- [x] Cards com meta + actions
- [x] Botões com ripple + shine
- [x] Carrinho sticky no lado direito
- [x] Animações suaves (.14s a .6s)
- [x] Tipografia (Playfair Display + Poppins)
- [x] Responsivo (1080px, 880px, 420px)

---

## 📦 Arquivos do Projeto

```
/Users/charm.sucre/Downloads/PROJETOS/
├── INDEX.HTML          # Estrutura HTML (hero + layout)
├── estilo.css          # Estilos e animações
├── head.js             # Lógica JS (produtos, carrinho)
├── img/                # Pasta para imagens
│   └── README.md
└── ESTRUTURA_FINAL.md  # Este arquivo
```

---

## 🚀 Como Usar

1. Coloque imagens em `./img/ninho.jpg`, `./img/banoffee.jpg`, etc.
2. Ou defina `window.minhasImagens` no HTML com URLs externas
3. Customize cores em `:root` do CSS
4. Adicione/remova produtos em `head.js` na array `const itens = [...]`

---

## 🎨 Customização Rápida

### Mudar cor da paleta (rosa → azul)
```css
:root{
  --accent-1: #0056b3;   /* Rosa → Azul */
  --accent-2: #0070e0;
  --accent-3: #b3d9ff;
}
```

### Aumentar/diminuir gap entre cards
```css
.shelf {
  gap: 24px;  /* Mude para 16px, 32px, etc */
}
```

### Desabilitar animações
```css
* {
  animation: none !important;
  transition: none !important;
}
```

---

**Desenvolvido para Charm sucrè — Confeitaria Gourmet** 🍰

