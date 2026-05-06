+praTiHub - Frontend
Português English

React Vite Tailwind CSS Vercel

Aplicação web construída com React + Vite e Tailwind CSS, integrada com backend Spring Boot.

🌐 Deploy em produção: maisprati-hub.vercel.app

🚀 Quick Start
Pré-requisitos
Node.js 18+
Backend rodando (maisprati-hub-server)
Configuração Inicial
Clone o repositório
git clone https://github.com/flaviare1s/maisprati-hub.git
cd maisprati-hub
Instale as dependências
npm install
Configure as variáveis de ambiente
Copie o arquivo .env.example para .env:

cp .env.example .env
Edite o arquivo .env com suas configurações:

VITE_API_BASE_URL=http://localhost:8080/api
Execute a aplicação
npm run dev
A aplicação estará disponível em http://localhost:5173

🏗️ Estrutura do Projeto
src/
├── assets/          # Imagens, ícones e arquivos estáticos
├── components/      # Componentes reutilizáveis (botões, cards, etc)
├── pages/          # Páginas com rotas (Home, Login, Dashboard, etc)
├── contexts/       # Contextos de estado global (Auth, Theme, etc)
├── hooks/          # Hooks customizados
├── services/       # Configuração de APIs e serviços
├── api/            # Funções de API organizadas por domínio
├── App.jsx         # Configuração de rotas
├── main.jsx        # Ponto de entrada da aplicação
└── index.css       # Estilos globais e configuração de temas
✨ Funcionalidades
🔐 Autenticação - Login, registro e autenticação social (Google)
📊 Dashboard - Painéis personalizados para estudantes e admins
👥 Teams - Sistema de equipes/guildas
📅 Calendário - Agendamento e gestão de reuniões
💬 Fórum - Sistema de posts e comentários
🔔 Notificações - Notificações em tempo real
👤 Perfil - Gerenciamento completo de perfil de usuário
🛠️ Tecnologias
React 18 - Biblioteca JavaScript para interfaces
Vite 5 - Build tool rápido e moderno
Tailwind CSS 3 - Framework CSS utilitário
React Router 6 - Roteamento client-side
Axios - Cliente HTTP
Day.js - Manipulação de datas
Vitest - Framework de testes
📝 Scripts Disponíveis
# Desenvolvimento
npm run dev

# Build para produção
npm run build

# Preview do build de produção
npm run preview

# Executar testes
npm run test # (Disponível apenas na branch test)

# Lint do código
npm run lint
🔗 Integração com Backend
Este frontend se conecta com a API Spring Boot. Certifique-se de:

Clonar e configurar o backend
Iniciar o MongoDB
Executar o backend na porta 8080
Configurar a variável VITE_API_BASE_URL no .env
Endpoints principais:

Backend API: http://localhost:8080/api
Swagger Docs: http://localhost:8080/swagger-ui/index.html

+praTiHub - Backend
🇧🇷 Português | 🇺🇸 English

Java Spring Boot MongoDB Docker

API RESTful construída com Java + Spring Boot e MongoDB, com autenticação JWT, perfis de ambiente e suporte a Docker.

🛠️ Tecnologias
Spring Boot 3.5 - Framework principal
MongoDB - Banco de dados NoSQL
Spring Security + JWT - Autenticação e autorização
BCrypt - Hashing de senhas
Swagger/OpenAPI - Documentação da API disponível em http://localhost:8080/swagger-ui/index.html
Docker - Containerização
Lombok - Redução de boilerplate
Maven - Gerenciamento de dependências
🚀 Quick Start
Pré-requisitos
Java 17
MongoDB Server
Docker e Docker Compose (opcional)
MongoDB Compass (opcional)
Configuração Inicial
Clone o repositório
git clone https://github.com/flaviare1s/maisprati-hub-server.git
cd maisprati-hub-server
Configure as variáveis de ambiente
Crie um arquivo .env na raiz do projeto:

JWT_SECRET=your_base64_encoded_secret_here
APP_FRONTEND_URL=http://localhost:3000
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GMAIL_API_REFRESH_TOKEN=your_gmail_refresh_token
EMAIL_FROM=your_email@gmail.com
**Inicie o MongoDB
Opção A - Usar Docker
docker-compose -f docker/docker-compose.dev.yml up -d
Opção B - Usar o MongoDB Server instalado no seu PC
Execute a aplicação
Perfil padrão (dev):

# Linux/Mac
./mvnw spring-boot:run

# Windows
.\mvnw.cmd spring-boot:run
Perfil dev (explícito):

# Linux/Mac
./mvnw spring-boot:run -Dspring-boot.run.profiles=dev

# Windows
.\mvnw.cmd spring-boot:run "-Dspring-boot.run.profiles=dev"
Perfil prod:

# Linux/Mac
./mvnw spring-boot:run -Dspring-boot.run.profiles=prod

# Windows
.\mvnw.cmd spring-boot:run "-Dspring-boot.run.profiles=prod"
A API estará disponível em http://localhost:8080

Documentação Swagger: http://localhost:8080/swagger-ui/index.html

🏗️ Arquitetura
O projeto segue uma arquitetura em camadas limpa e bem definida:

src/main/java/com/maisprati/hub/
├── presentation/         # Controllers e DTOs de API
├── application/          # Serviços e lógica de negócio
├── domain/              # Entidades e enums
└── infrastructure/      # Repositórios, segurança e configurações
Fluxo de Requisição
Cliente → Controller → Service → Repository → MongoDB
🔐 Autenticação
O sistema utiliza JWT (JSON Web Tokens) para autenticação.

Papéis de Usuário
ADMIN - Acesso administrativo completo
STUDENT - Acesso de estudante
Endpoints Públicos
POST /api/auth/register - Registro de novo usuário
POST /api/auth/login - Login e obtenção do token JWT
Endpoints Protegidos
Requerem header de autorização:

Authorization: Bearer <seu_token_jwt>
Método	Endpoint	Acesso	Descrição
GET	/api/users	ADMIN	Listar todos os usuários
GET	/api/users/{id}	ADMIN ou próprio usuário	Obter usuário específico
PUT	/api/users/{id}	ADMIN ou próprio usuário	Atualizar usuário
DELETE	/api/users/{id}	ADMIN	Remover usuário
🐳 Docker
Comandos Úteis
# Iniciar containers
docker-compose -f docker/docker-compose.dev.yml up -d

# Parar containers (mantém dados)
docker-compose -f docker/docker-compose.dev.yml stop

# Reiniciar containers
docker-compose -f docker/docker-compose.dev.yml start

# Parar e remover containers (mantém volumes)
docker-compose -f docker/docker-compose.dev.yml down

# Parar e remover tudo (incluindo dados)
docker-compose -f docker/docker-compose.dev.yml down -v

# Acessar shell do MongoDB
docker exec -it mongodev mongosh -u admin -p admin123 --authenticationDatabase admin
Conexão MongoDB
Via MongoDB Compass:

mongodb://admin:admin123@localhost:27017/maisprati-hub
Configuração local (sem Docker):

mongodb://localhost:27017/maisprati-hub
📝 Desenvolvimento
Build do Projeto
./mvnw clean install
Executar Testes
./mvnw test
Perfis de Ambiente
dev (padrão) - Desenvolvimento local
prod - Produção (MongoDB Atlas)
Lombok
O projeto utiliza Lombok para reduzir código boilerplate.

VS Code: Instale a extensão Lombok Annotations Support

IntelliJ IDEA:

Instale o plugin Lombok (Settings → Plugins → Marketplace)
Habilite Annotation Processing (Settings → Build, Execution, Deployment → Compiler → Annotation Processors)
