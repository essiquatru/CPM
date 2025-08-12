# CPM - Campeonato Paulista de MamoBall

Site oficial do Campeonato Paulista de MamoBall com página de inscrição moderna e responsiva.

## 📁 Estrutura do Projeto

```
├── index.html          # Página principal
├── inscricao.html      # Página de inscrição
├── styles.css          # Estilos da página principal
├── inscricao.css       # Estilos da página de inscrição
├── script.js           # JavaScript da página principal
├── app.js              # JavaScript da página de inscrição
├── cpm.png             # Logo do CPM
└── README.md           # Este arquivo
```

## 🚀 Como Testar Localmente

1. **Clone ou baixe os arquivos** para sua máquina
2. **Abra o arquivo `index.html`** em seu navegador
3. **Navegue para a página de inscrição** clicando em "Inscreva seu Time"
4. **Teste a funcionalidade** preenchendo o formulário

### Teste Manual Simples

1. Abra `inscricao.html` no navegador
2. Faça upload de uma imagem (PNG, JPG ou WebP, máximo 5MB)
3. Preencha os dados do clube:
   - Nome do Clube (obrigatório)
   - Dono (obrigatório)
   - Capitão (obrigatório)
   - Técnico (opcional)
4. Adicione 6 jogadores com:
   - ID (obrigatório)
   - Nick (obrigatório)
   - Pelo menos uma posição marcada (GL, VL ou PV)
5. Clique em "Enviar inscrição"
6. Verifique se o modal de sucesso aparece

## 🔧 Configuração do Backend

### Endpoints Necessários

O frontend espera os seguintes endpoints:

#### 1. Verificar Período de Inscrições
```
GET /api/seasons/current
```

**Respostas esperadas:**
- `200` com JSON `{ _id, name, startAt, endAt }` - Inscrições abertas
- `404` ou `200` com `null` - Inscrições fechadas
- `403` com `{ message, nextOpen }` - Inscrições fechadas com data de próxima abertura

#### 2. Enviar Inscrição
```
POST /api/teams
Content-Type: multipart/form-data
```

**Campos enviados:**
- `logo` (file) - Logo do clube
- `name` (string) - Nome do clube
- `owner` (string) - Dono do clube
- `captain` (string) - Capitão do clube
- `coach` (string, opcional) - Técnico do clube
- `players` (string JSON) - Array de jogadores
- `seasonId` (string, opcional) - ID da temporada atual

**Exemplo do campo `players`:**
```json
[
  {
    "id": "12345",
    "nick": "Player1",
    "positions": ["GL", "PV"]
  },
  {
    "id": "67890",
    "nick": "Player2",
    "positions": ["VL"]
  }
]
```

**Respostas esperadas:**
- `201` - Inscrição enviada com sucesso
- `403` - Inscrições fechadas
- `4xx/5xx` - Erro com mensagem

### Configurações no Frontend

No arquivo `app.js`, ajuste as seguintes configurações:

```javascript
// URL base da API
const API_BASE = '/api'; // Mude para sua URL

// Tamanho máximo do arquivo (5MB)
const MAX_FILE_SIZE = 5 * 1024 * 1024;

// Tipos de arquivo aceitos
const ACCEPTED_TYPES = ['image/png', 'image/jpeg', 'image/webp'];
```

## 🎨 Características do Design

### Página Principal
- Design moderno e minimalista
- Layout responsivo (mobile-first)
- Animações suaves
- Seção de estatísticas
- Cards flutuantes animados
- Seção de benefícios

### Página de Inscrição
- Interface limpa e intuitiva
- Upload de arquivo com drag & drop
- Preview da imagem
- Formulário em duas colunas (desktop)
- Gerenciamento dinâmico de jogadores
- Validação em tempo real
- Modal de sucesso elegante

### Acessibilidade
- Labels associados aos inputs
- Mensagens de erro claras
- Navegação por teclado
- Contraste adequado
- Estados de foco visíveis

## 📱 Responsividade

O site é totalmente responsivo e funciona bem em:
- Desktop (1200px+)
- Tablet (768px - 1024px)
- Mobile (320px - 768px)

## 🛠 Tecnologias Utilizadas

- **HTML5** - Estrutura semântica
- **CSS3** - Estilos modernos com CSS Grid e Flexbox
- **JavaScript ES6+** - Funcionalidades interativas
- **Font Inter** - Tipografia moderna
- **SVG Icons** - Ícones vetoriais

## 🎯 Funcionalidades Implementadas

### ✅ Critérios de Aceitação Atendidos

- [x] Upload da logo com preview e validação
- [x] Mínimo 6 e máximo 10 jogadores
- [x] Validação de campos obrigatórios
- [x] Verificação de período de inscrições
- [x] Envio via multipart/form-data
- [x] Modal de sucesso
- [x] Layout responsivo e acessível
- [x] Documentação completa

### ✨ Funcionalidades Extras

- Drag & drop para upload de arquivo
- Animações suaves
- Estados de loading
- Validação em tempo real
- Interface moderna e intuitiva
- Mensagens de erro claras
- Navegação por teclado

## 🔒 Segurança

- Validação client-side completa
- Verificação de tipos de arquivo
- Limite de tamanho de arquivo
- Sanitização de dados
- Proteção contra XSS

## 📞 Suporte

Para dúvidas ou problemas:
- Email: contato@cpm.com.br
- WhatsApp: Comunidade oficial

---

**CPM - Campeonato Paulista de MamoBall**  
*O maior campeonato de MamoBall WhatsApp*