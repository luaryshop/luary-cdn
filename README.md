[readme_md.md](https://github.com/user-attachments/files/34217457/readme_md.md)
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

## 3. Como a URL é construída via jsDelivr

O painel administrativo (`admin.html`) gera automaticamente as URLs apontando para a CDN com base no seguinte formato base:

```
https://cdn.jsdelivr.net/gh/luaryshop/luary-cdn@main/products/{SKU}/{NUMERO}.webp
```

Exemplo real para a foto principal do SKU `CH-001`:

```
https://cdn.jsdelivr.net/gh/luaryshop/luary-cdn@main/products/CH-001/01.webp
```

---

## 4. Gerenciamento de Cache do jsDelivr

- O jsDelivr armazena os arquivos em cache por até 7 dias na branch `@main`.
- Caso substitua uma imagem e precise forçar a atualização imediata na vitrine, utilize a API de purge do jsDelivr acessando a URL correspondente:
  ```
  https://purge.jsdelivr.net/gh/luaryshop/luary-cdn@main/products/CH-001/01.webp
  ```
