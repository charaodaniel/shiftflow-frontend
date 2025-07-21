# ShiftFlow Frontend

Frontend do sistema ShiftFlow refatorado - Sistema completo para gestão de escalas, funcionários e motoristas.

## 🚀 Tecnologias

- **HTML5** - Estrutura das páginas
- **Tailwind CSS** - Framework CSS utilitário
- **JavaScript Puro** - Funcionalidades e interações
- **Vercel** - Plataforma de deploy

## 📁 Estrutura do Projeto

```
shiftflow-frontend/
├── public/
│   ├── css/
│   │   └── style.css          # CSS compilado do Tailwind
│   ├── js/
│   │   ├── config.js          # Configurações da aplicação
│   │   ├── utils/             # Utilitários
│   │   │   ├── api.js         # Cliente HTTP e autenticação
│   │   │   ├── forms.js       # Validação e manipulação de formulários
│   │   │   ├── notifications.js # Sistema de notificações
│   │   │   └── theme.js       # Gerenciamento de temas
│   │   └── modules/           # Módulos específicos
│   │       ├── auth.js        # Módulo de autenticação
│   │       └── dashboard.js   # Módulo do dashboard
│   └── images/                # Imagens e assets
├── pages/
│   ├── index.html             # Página inicial
│   ├── login.html             # Página de login
│   ├── register.html          # Página de registro
│   ├── dashboard.html         # Dashboard principal
│   ├── employees.html         # Gestão de funcionários
│   ├── drivers.html           # Gestão de motoristas
│   ├── vehicles.html          # Gestão de veículos
│   ├── schedules.html         # Gestão de escalas
│   └── reports.html           # Relatórios
├── src/
│   └── input.css              # CSS de entrada do Tailwind
├── package.json               # Dependências e scripts
├── tailwind.config.js         # Configuração do Tailwind
├── vercel.json                # Configuração da Vercel
└── README.md                  # Este arquivo
```

## 🛠️ Desenvolvimento Local

### Pré-requisitos

- Node.js 16+ 
- npm ou yarn

### Instalação

```bash
# Clonar o repositório
git clone https://github.com/seu-usuario/shiftflow-frontend.git
cd shiftflow-frontend

# Instalar dependências
npm install

# Compilar CSS do Tailwind
npm run build

# Iniciar servidor de desenvolvimento
npm start
```

O servidor estará disponível em `http://localhost:3000`

### Scripts Disponíveis

```bash
# Compilar CSS para produção (minificado)
npm run build

# Compilar CSS em modo de desenvolvimento (com watch)
npm run dev

# Iniciar servidor local
npm start

# Visualizar build de produção
npm run preview
```

## 🌐 Deploy na Vercel

### Configuração Automática

1. **Fork/Clone do Repositório:**
   ```bash
   git clone https://github.com/seu-usuario/shiftflow-frontend.git
   cd shiftflow-frontend
   ```

2. **Push para GitHub:**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

3. **Deploy na Vercel:**
   - Acesse [vercel.com](https://vercel.com)
   - Conecte sua conta GitHub
   - Importe o repositório `shiftflow-frontend`
   - Configure as variáveis de ambiente (ver seção abaixo)
   - Deploy automático!

### Variáveis de Ambiente

Configure as seguintes variáveis na Vercel:

```env
NEXT_PUBLIC_API_URL=http://62.72.9.108:3001
NEXT_PUBLIC_APP_NAME=ShiftFlow
NODE_ENV=production
```

### Configuração de Domínio Personalizado

1. **Na Vercel:**
   - Vá para Settings > Domains
   - Adicione seu domínio personalizado

2. **No seu provedor DNS:**
   - Adicione um registro CNAME apontando para `cname.vercel-dns.com`

## 🔧 Configuração da API

O frontend se conecta ao backend através das configurações em `public/js/config.js`:

```javascript
const CONFIG = {
  API_BASE_URL: 'http://62.72.9.108:3001', // URL do backend
  // ... outras configurações
};
```

### Endpoints Principais

- **Autenticação:** `/auth/login`, `/auth/register`, `/auth/logout`
- **Dashboard:** `/api/dashboard/stats`, `/api/dashboard/activities`
- **Funcionários:** `/api/employees`
- **Motoristas:** `/api/drivers`
- **Veículos:** `/api/vehicles`
- **Escalas:** `/api/schedules`
- **Relatórios:** `/api/reports`

## 🎨 Personalização

### Temas

O sistema suporta temas claro/escuro com persistência:

```javascript
// Alternar tema
themeManager.toggleTheme();

// Definir tema específico
themeManager.setTheme('dark'); // 'light', 'dark', 'system'

// Verificar tema atual
const isDark = themeManager.isDarkMode();
```

### Cores

Personalize as cores no `tailwind.config.js`:

```javascript
theme: {
  extend: {
    colors: {
      primary: {
        500: '#3b82f6', // Cor primária
        600: '#2563eb',
        // ...
      }
    }
  }
}
```

## 📱 Responsividade

O sistema é totalmente responsivo com breakpoints:

- **Mobile:** < 640px
- **Tablet:** 640px - 1024px  
- **Desktop:** > 1024px

## 🔒 Segurança

### Autenticação

- JWT tokens armazenados no localStorage
- Refresh automático de tokens
- Proteção de rotas automática
- Logout automático em caso de token inválido

### Headers de Segurança

Configurados no `vercel.json`:

```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        { "key": "X-Content-Type-Options", "value": "nosniff" },
        { "key": "X-Frame-Options", "value": "DENY" },
        { "key": "X-XSS-Protection", "value": "1; mode=block" }
      ]
    }
  ]
}
```

## 🚀 Performance

### Otimizações Implementadas

- **CSS minificado** com Tailwind CSS
- **Cache de assets** configurado
- **Lazy loading** de imagens
- **Compressão gzip** automática na Vercel
- **CDN global** da Vercel

### Métricas de Performance

- **First Contentful Paint:** < 1.5s
- **Largest Contentful Paint:** < 2.5s
- **Time to Interactive:** < 3.5s
- **Cumulative Layout Shift:** < 0.1

## 🐛 Debugging

### Logs de Desenvolvimento

```javascript
// Habilitar logs de debug
CONFIG.DEBUG = true;

// Logs da API
console.log('API Response:', response);

// Logs de autenticação
console.log('User authenticated:', auth.isAuthenticated());
```

### Ferramentas de Debug

- **Console do navegador** para logs JavaScript
- **Network tab** para requisições HTTP
- **Vercel Analytics** para métricas de performance
- **Vercel Logs** para logs de deploy

## 📊 Monitoramento

### Analytics

- **Vercel Analytics** habilitado
- **Performance metrics** automáticas
- **Error tracking** integrado

### Health Checks

```javascript
// Verificar status do backend
async function checkBackendStatus() {
  const response = await fetch(CONFIG.API_BASE_URL + '/health');
  return response.ok;
}
```

## 🤝 Contribuição

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 📞 Suporte

- **Email:** suporte@shiftflow.com.br
- **GitHub Issues:** [Reportar Bug](https://github.com/seu-usuario/shiftflow-frontend/issues)
- **Documentação:** [Wiki do Projeto](https://github.com/seu-usuario/shiftflow-frontend/wiki)

---

**Desenvolvido com ❤️ pela equipe ShiftFlow**

