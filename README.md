# 💰 Pague Stream

<div align="center">

![Pague Stream](https://img.shields.io/badge/Pague%20Stream-v1.0.0-purple)
![Node.js](https://img.shields.io/badge/Node.js-18%2B-green)
![TypeScript](https://img.shields.io/badge/TypeScript-5.7-blue)
![Next.js](https://img.shields.io/badge/Next.js-15-black)
![Fastify](https://img.shields.io/badge/Fastify-5.3-orange)

**Plataforma completa para streamers receberem pagamentos PIX durante transmissões ao vivo**

🌐 **[Acesse o site em produção](https://paguestream.com/)** • [Funcionalidades](#-funcionalidades) • [Tecnologias](#-tecnologias) • [Arquitetura](#-arquitetura) • [Demonstração](#-demonstração)

</div>

---

## 📖 Sobre o Projeto

O **Pague Stream** é uma plataforma inovadora desenvolvida para facilitar a monetização de streamers e criadores de conteúdo. O sistema permite receber doações via PIX em tempo real durante transmissões ao vivo, com alertas personalizados, integração com plataformas populares de streaming e um painel completo de gerenciamento.

### 🎯 Objetivo

Facilitar a conexão entre criadores de conteúdo e sua comunidade, oferecendo uma solução segura, rápida e personalizável para recebimento de doações durante lives, sem expor dados pessoais dos doadores.

### 🌟 Destaques

- ⚡ **Tempo Real**: Processamento instantâneo de pagamentos PIX
- 🎨 **Personalização**: Widgets totalmente customizáveis
- 🤖 **IA Integrada**: Moderação de conteúdo e text-to-speech
- 📊 **Analytics**: Dashboard completo com métricas e insights
- 🔗 **Integrações**: StreamElements, StreamLabs e sistema próprio

---

## ✨ Funcionalidades

### 💳 Sistema de Pagamentos
- ✅ Processamento de pagamentos PIX em tempo real
- ✅ Integração com gateway de pagamento (ExpaySolutions/PagueSafe)
- ✅ Cálculo automático de taxas
- ✅ Histórico completo de transações
- ✅ Sistema de saques automatizado

### 🎨 Widgets Personalizáveis
- **Widget de Alerta**: Exibe notificações de doações com animações e áudio
- **Widget de QR Code**: Gera QR code para checkout rápido
- Personalização completa de cores, estilos e comportamentos
- Atualização em tempo real via WebSocket

### 🤖 Inteligência Artificial
- **Moderação de Conteúdo**: Filtragem automática com OpenAI
- **Text-to-Speech**: Conversão de mensagens em áudio com Cartesia
- **Correção Gramatical**: Melhoria automática de textos para áudio

### 📊 Dashboard e Analytics
- Painel em tempo real de todas as doações
- Métricas e insights sobre performance
- Análise de melhores dias/horários
- Gráficos e visualizações interativas
- Sistema de relatórios financeiros

### 🔗 Integrações
- **StreamElements**: Integração nativa para alertas
- **StreamLabs**: Integração nativa para alertas
- **Sistema Próprio**: Widgets standalone para OBS

### ⚙️ Recursos Adicionais
- Sistema de saques com validação
- Upload e validação de documentos
- Notificações por email transacionais
- WebSocket para atualizações em tempo real
- Sistema de feedback integrado

---

## 🛠️ Tecnologias

### Backend
- **Fastify** - Framework web rápido e eficiente
- **TypeScript** - Type safety e melhor DX
- **MongoDB** - Banco de dados NoSQL
- **WebSocket** - Comunicação em tempo real
- **Clerk** - Autenticação e gerenciamento de usuários
- **Prisma** - ORM para gerenciamento de dados

### Frontend
- **Next.js 15** - Framework React com App Router
- **React 19** - Biblioteca UI moderna
- **Tailwind CSS** - Estilização utility-first
- **Radix UI** - Componentes acessíveis
- **TanStack Query** - Gerenciamento de estado servidor
- **Framer Motion** - Animações fluidas

### Widgets
- **React** - Biblioteca UI
- **Vite** - Build tool rápido
- **Framer Motion** - Animações fluidas
- **QRCode.react** - Geração de QR codes

### Infraestrutura
- **Turborepo** - Gerenciamento de monorepo
- **pnpm** - Gerenciador de pacotes eficiente
- **Docker** - Containerização
- **AWS S3** - Armazenamento de arquivos

### Serviços Externos
- **AWS S3** - Armazenamento de arquivos (áudios)
- **OpenAI** - Moderação de conteúdo
- **Cartesia** - Text-to-speech
- **Resend** - Envio de emails transacionais
- **Clerk** - Autenticação e gerenciamento de usuários

---

## 🏗️ Arquitetura

O projeto utiliza uma arquitetura **monorepo** com Turborepo, organizado em múltiplas aplicações:

```
pague-stream/
├── apps/
│   ├── api/                 # Backend API (Fastify + TypeScript)
│   │   ├── src/
│   │   │   ├── modules/     # Módulos da API
│   │   │   │   ├── transactions/
│   │   │   │   ├── configs/
│   │   │   │   ├── dashboard/
│   │   │   │   ├── webhooks/
│   │   │   │   └── websocket/
│   │   │   ├── services/    # Serviços externos
│   │   │   ├── shared/      # Código compartilhado
│   │   │   └── server.ts    # Servidor principal
│   │   └── docker-compose.yml
│   │
│   ├── web-app/             # Frontend (Next.js 15)
│   │   ├── src/
│   │   │   ├── app/         # Rotas e páginas
│   │   │   ├── components/  # Componentes React
│   │   │   ├── requests/    # Chamadas à API
│   │   │   └── services/    # Serviços
│   │   └── public/          # Arquivos estáticos
│   │
│   ├── widgets/             # Widgets para streaming
│   │   ├── src/
│   │   │   ├── pages/       # Páginas dos widgets
│   │   │   │   ├── alert.tsx
│   │   │   │   └── qr-code.tsx
│   │   │   └── services/    # Serviços
│   │   └── public/
│   │
│   └── migrations/          # Scripts de migração
│
└── packages/
    └── types/               # Tipos TypeScript compartilhados
```

### Fluxo de Dados

1. **Pagamento**: Usuário faz doação via checkout → Gateway PIX → Webhook → API
2. **Processamento**: API processa pagamento → Moderação de conteúdo → Text-to-speech
3. **Notificação**: WebSocket notifica widgets → Alerta exibido na transmissão
4. **Dashboard**: Dados atualizados em tempo real → Métricas calculadas

---

## 📸 Demonstração

### 🌐 Site em Produção

**Acesse o site em produção:** [https://paguestream.com/](https://paguestream.com/)

O site está totalmente funcional e em produção, oferecendo:
- ✅ Checkout personalizado para doações
- ✅ Widgets de alerta e QR code
- ✅ Dashboard em tempo real
- ✅ Métricas e analytics
- ✅ Integrações com StreamElements e StreamLabs

### Screenshots do Projeto

#### 📊 Dashboard em Tempo Real
Visualização de todas as doações conforme chegam, com controle total sobre o que será exibido na transmissão.

![Dashboard](./screenshots/dashboard.jpeg)

#### 📈 Métricas e Analytics
Análise completa de performance com gráficos interativos e insights sobre melhores horários e dias.

![Métricas](./screenshots/metrics.png)

#### ⚙️ Configurações
Personalização completa de widgets, alertas e checkout com interface intuitiva.

![Configurações](./screenshots/settings.png)

#### 📄 Validação de Documentos (KYC)
Sistema completo de upload e validação de documentos para segurança e conformidade.

![KYC](./screenshots/kyc.png)

#### 🎨 Widget de Alerta
Notificações animadas e personalizáveis que aparecem durante a transmissão ao vivo.

![Widget de Alerta](./screenshots/widget-alert.png)

#### 📱 Widget de QR Code
QR Code dinâmico para checkout rápido e fácil durante a transmissão.

![Widget QR Code](./screenshots/widget-qrcode.png)

### Funcionalidades em Ação

- **Dashboard em Tempo Real**: Visualização de doações conforme chegam
- **Widget de Alerta**: Notificações animadas durante a transmissão
- **Widget de QR Code**: Checkout rápido via QR code
- **Painel de Métricas**: Gráficos e análises de performance
- **Configurações**: Personalização completa de widgets

---

## 🎯 Desafios e Soluções

### Desafios Enfrentados

1. **Processamento em Tempo Real**
   - **Solução**: Implementação de WebSocket para comunicação bidirecional
   - **Resultado**: Atualizações instantâneas em todos os clientes

2. **Moderação de Conteúdo**
   - **Solução**: Integração com OpenAI para filtragem automática
   - **Resultado**: Conteúdo inapropriado bloqueado antes de ser exibido

3. **Text-to-Speech de Qualidade**
   - **Solução**: Integração com Cartesia para áudio natural
   - **Resultado**: Mensagens convertidas em áudio com voz realista

4. **Arquitetura Escalável**
   - **Solução**: Monorepo com Turborepo para gerenciamento eficiente
   - **Resultado**: Build e deploy otimizados

---

## 📊 Métricas do Projeto

- **Status**: ✅ **Em Produção** - [paguestream.com](https://paguestream.com/)
- **Tempo de Desenvolvimento**: Projeto completo e funcional
- **Arquitetura**: Monorepo com 3 aplicações principais
- **Tecnologias**: 15+ tecnologias integradas
- **Linhas de Código**: ~300k+ linhas
- **Módulos**: 10+ módulos na API
- **Usuários**: Sistema em uso por streamers

---

## 🔐 Segurança

- Autenticação via Clerk com JWT
- Validação de dados com Zod
- Sanitização de conteúdo com OpenAI
- CORS configurado adequadamente
- Variáveis de ambiente protegidas

---

## 🚀 Performance

- **API**: Fastify para alta performance
- **Frontend**: Next.js 15 com App Router para SSR/SSG
- **Widgets**: Vite para build otimizado
- **WebSocket**: Comunicação eficiente em tempo real
- **Cache**: TanStack Query para cache inteligente

---

## 📚 Aprendizados

Este projeto proporcionou experiência significativa em:

- Arquitetura de monorepo com Turborepo
- Integração de múltiplos serviços externos
- Desenvolvimento de widgets para streaming
- Processamento de pagamentos em tempo real
- Implementação de WebSocket para comunicação bidirecional
- Uso de IA para moderação de conteúdo
- Text-to-speech com qualidade profissional

---

## 👨‍💻 Desenvolvimento

Desenvolvido como projeto full-stack completo, demonstrando habilidades em:

- ✅ Arquitetura de software escalável
- ✅ Integração de APIs e serviços externos
- ✅ Desenvolvimento frontend e backend
- ✅ Gerenciamento de estado complexo
- ✅ Comunicação em tempo real
- ✅ Integração com IA
- ✅ Processamento de pagamentos

---

## 🔗 Links

- **Site em Produção**: [paguestream.com](https://paguestream.com/)
- **Repositório Privado**: [paguestream_sistema](https://github.com/anthonymengottii/paguestream_sistema) (acesso restrito)

---

## 📝 Nota

Este é um projeto de portfólio que demonstra habilidades em desenvolvimento full-stack. O código-fonte completo está em repositório privado por questões de segurança e propriedade intelectual.

---

<div align="center">

**Desenvolvido com ❤️ para facilitar a monetização de streamers através de pagamentos PIX em tempo real.**

🌐 **[Acesse o site em produção](https://paguestream.com/)**

</div>

