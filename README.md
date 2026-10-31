# luary-cdn

Banco de imagens independente para **luaryshop.github.io/luary-system**, servido gratuitamente via **jsDelivr** a partir deste repositório GitHub.

---

## 1. Estrutura de Pastas

Para manter a organização impecável e escalável, cada referência (SKU) possui sua própria pasta individual dentro de `products/`, contendo até 10 imagens otimizadas em formato WebP:

```
luary-cdn/
├── categories/
├── home/
├── products/
│   ├── CH-001/
│   │   ├── 01.webp       (Imagem principal do produto)
│   │   ├── 02.webp       (Imagem secundária)
│   │   └── ...           (Até 10.webp)
│   └── LUA-1020/
│       ├── 01.webp
│       └── 02.webp
├── settings/
└── subcategorias/
```

> **Nota:** Mantenha os nomes das pastas em maiúsculas e exatamente iguais ao SKU cadastrado no painel administrativo (`admin.html`).

---

## 2. Regra de Nomenclatura e Formato

Dentro da pasta de cada SKU, as imagens devem seguir estritamente este padrão:
- Formato: **WebP** (`.webp`)
- Nomenclatura sequencial com dois dígitos: `01.webp`, `02.webp`, `03.webp`... até `10.webp`.

---

## 3. Como publicar imagens

Use o **gerenciador de imagens** do painel (`cdn.html` no luary-system): ele converte para WebP, grava no repositório em um único commit e, nos produtos, atualiza o campo `images` no Firestore. O acesso exige login no painel **e** um token fine-grained do GitHub restrito a este repositório (*Contents: Read and write*), mantido apenas na memória da aba.

Alternativa sem token: `editor.html` gera um ZIP para enviar manualmente ao GitHub.

---

## 4. Como a URL é construída via jsDelivr

URLs geradas pelo gerenciador são **fixadas no commit** (imutáveis, sem cache desatualizado):

```
https://cdn.jsdelivr.net/gh/luaryshop/luary-cdn@{COMMIT_SHA}/products/{SKU}/01.webp
```

URLs antigas em `@main` continuam funcionando, mas o jsDelivr pode manter uma versão em cache por até 7 dias após uma substituição. Para forçar a atualização:

```
https://purge.jsdelivr.net/gh/luaryshop/luary-cdn@main/products/CH-001/01.webp
```
