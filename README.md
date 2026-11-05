
# 🔳 Gerador de QR Codes para E-commerces com Node.Js

API em **Node.js** para gerar QR Codes de forma rápida e personalizável, pensada para lojas virtuais: links de produtos, cupons de desconto, páginas de checkout, rastreio de pedidos, perfis de redes sociais e muito mais.

---

## 📌 Sobre o projeto

Lojas online precisam conectar o mundo físico ao digital: embalagens, cartões de agradecimento, panfletos, vitrines e etiquetas. Este projeto resolve isso oferecendo um serviço simples que recebe uma URL (ou qualquer texto) e devolve um QR Code pronto para uso.

### Principais funcionalidades

- Geração de QR Code a partir de qualquer URL ou texto
- Retorno em **PNG**, **SVG** ou **Data URL (Base64)**
- Personalização de tamanho, margem e cores
- Validação dos dados de entrada
- Tratamento de erros com mensagens claras
- Pronto para ser integrado a qualquer e-commerce via requisição HTTP

---

## 🛠️ Tecnologias

- [Node.js](https://nodejs.org/)
- [qrcode](https://www.npmjs.com/package/qrcode) (geração dos QR Codes)
- Git e GitHub para versionamento

> Ajuste esta lista conforme as bibliotecas que você realmente usou (Express, Fastify, TypeScript, Zod, etc.).

---

## 📋 Pré-requisitos

- [Node.js](https://nodejs.org/) 18 ou superior
- npm (ou yarn/pnpm)

---

## 🚀 Como executar

```bash
# 1. Clone o repositório
git clone https://github.com/edusilverfit/NOME-DO-REPOSITORIO.git

# 2. Entre na pasta do projeto
cd NOME-DO-REPOSITORIO

# 3. Instale as dependências
npm install

# 4. Configure as variáveis de ambiente
cp .env.example .env

# 5. Inicie o servidor
npm run dev
```

O servidor ficará disponível em `http://localhost:3000`.

---

## ⚙️ Variáveis de ambiente

| Variável | Descrição | Padrão |
|----------|-----------|--------|
| `PORT` | Porta em que a API vai rodar | `3000` |

---

## 📡 Uso da API

### Gerar QR Code

**`POST /qrcode`**

#### Corpo da requisição

```json
{
  "url": "https://minhaloja.com.br/produto/camiseta-azul",
  "format": "png",
  "size": 300,
  "margin": 2,
  "color": {
    "dark": "#000000",
    "light": "#FFFFFF"
  }
}
```

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|-------------|-----------|
| `url` | string | ✅ | URL ou texto que será codificado |
| `format` | string | ❌ | `png`, `svg` ou `base64` (padrão: `png`) |
| `size` | number | ❌ | Largura em pixels (padrão: `300`) |
| `margin` | number | ❌ | Margem ao redor do código (padrão: `2`) |
| `color.dark` | string | ❌ | Cor dos módulos do QR Code |
| `color.light` | string | ❌ | Cor do fundo |

#### Exemplo com cURL

```bash
curl -X POST http://localhost:3000/qrcode \
  -H "Content-Type: application/json" \
  -d '{"url": "https://minhaloja.com.br/produto/camiseta-azul", "format": "base64"}'
```

#### Resposta de sucesso

```json
{
  "qrcode": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..."
}
```

#### Resposta de erro

```json
{
  "error": "O campo 'url' é obrigatório."
}
```

---

## 🛒 Casos de uso em e-commerce

- **Embalagens:** QR Code que leva o cliente à página de avaliação do produto
- **Cupons de desconto:** código impresso no pedido para a próxima compra
- **Rastreio:** link direto para o acompanhamento da entrega
- **Fidelização:** acesso rápido ao Instagram, WhatsApp ou programa de pontos
- **Loja física + online:** etiquetas de produtos que levam ao catálogo digital

---

## 📁 Estrutura do projeto

```
├── src/
│   ├── routes/        # Rotas da API
│   ├── services/      # Lógica de geração do QR Code
│   └── server.js      # Ponto de entrada
├── .env.example
├── package.json
└── README.md
```

> Atualize a estrutura conforme as pastas do seu projeto.

---

## 🧪 Testes

```bash
npm test
```

---

## 🗺️ Próximos passos

- [ ] Inserir logo da loja no centro do QR Code
- [ ] Autenticação por API key
- [ ] Geração em lote (vários QR Codes por requisição)
- [ ] Rate limiting
- [ ] Documentação interativa com Swagger
- [ ] Deploy em nuvem

---

## 🤝 Como contribuir

1. Faça um fork do projeto
2. Crie uma branch: `git checkout -b feature/minha-feature`
3. Commit suas mudanças: `git commit -m "feat: minha feature"`
4. Envie para o repositório: `git push origin feature/minha-feature`
5. Abra um Pull Request

---

## 👨‍💻 Autor

**Eduardo Akere**
Desenvolvedor Back-end | Node.js

- GitHub: [@edusilverfit](https://github.com/edusilverfit)
- LinkedIn: www.linkedin.com/in/eduardoakere

---

## 📄 Licença

Este projeto está sob a licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.
