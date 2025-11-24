# 🏗️ Arquitetura do Pague Stream

## Visão Geral

O Pague Stream é construído como um **monorepo** utilizando Turborepo, permitindo gerenciamento eficiente de múltiplas aplicações relacionadas.

## Estrutura do Monorepo

### Aplicações

1. **API** (`apps/api`)
   - Backend em Fastify
   - TypeScript
   - MongoDB como banco de dados
   - WebSocket para comunicação em tempo real

2. **Web App** (`apps/web-app`)
   - Frontend em Next.js 15
   - React 19
   - App Router
   - Tailwind CSS

3. **Widgets** (`apps/widgets`)
   - Widgets standalone para streaming
   - React + Vite
   - Integração com OBS

4. **Migrations** (`apps/migrations`)
   - Scripts de migração do banco de dados

### Pacotes Compartilhados

- **Types** (`packages/types`)
  - Tipos TypeScript compartilhados
  - Schemas de validação
  - DTOs

## Fluxo de Dados

### 1. Processamento de Pagamento

```
Cliente → Checkout → Gateway PIX → Webhook → API → MongoDB
                                              ↓
                                         WebSocket
                                              ↓
                                    Widgets (Alertas)
```

### 2. Comunicação em Tempo Real

```
API (WebSocket Server)
    ↕
Web App (WebSocket Client)
    ↕
Widgets (WebSocket Client)
```

### 3. Pipeline de Processamento

```
Pagamento Recebido
    ↓
Validação
    ↓
Moderação de Conteúdo (OpenAI)
    ↓
Correção Gramatical (OpenAI)
    ↓
Text-to-Speech (Cartesia)
    ↓
Upload para S3
    ↓
Notificação via WebSocket
    ↓
Exibição no Widget
```

## Tecnologias por Camada

### Backend
- **Framework**: Fastify
- **Linguagem**: TypeScript
- **Banco de Dados**: MongoDB
- **ORM**: Prisma (quando aplicável)
- **Autenticação**: Clerk
- **WebSocket**: @fastify/websocket

### Frontend
- **Framework**: Next.js 15
- **UI Library**: React 19
- **Styling**: Tailwind CSS
- **Components**: Radix UI
- **State Management**: TanStack Query
- **Forms**: React Hook Form
- **Validation**: Zod

### Infraestrutura
- **Monorepo**: Turborepo
- **Package Manager**: pnpm
- **Containerização**: Docker
- **Storage**: AWS S3
- **CDN**: CloudFront (opcional)

## Padrões de Código

### Estrutura de Módulos (API)

```
modules/
├── transactions/
│   ├── transactions.controller.ts
│   └── transactions.routes.ts
├── configs/
│   ├── configs.controller.ts
│   └── configs.routes.ts
└── ...
```

### Estrutura de Componentes (Frontend)

```
components/
├── ui/              # Componentes base
├── app-*            # Componentes específicos do app
└── ...
```

## Segurança

- Autenticação via Clerk
- Validação de dados com Zod
- Sanitização de conteúdo
- CORS configurado
- Variáveis de ambiente protegidas

## Performance

- Build otimizado com Turborepo
- Cache inteligente com TanStack Query
- Lazy loading de componentes
- Code splitting automático (Next.js)
- WebSocket eficiente para tempo real

