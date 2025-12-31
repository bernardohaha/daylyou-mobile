# daylyou-mobile
# Daylyou Mobile

<div align="center">
  <h3>Uma aplicação de registo consciente da vida quotidiana</h3>
  <p>Preserva presença. Constrói memória pessoal. Valoriza o presente.</p>
</div>

---

## 📖 Sobre o Projeto

**Daylyou** é uma aplicação mobile progressiva (PWA) dedicada ao auto-conhecimento, registo visual e estatístico da vida e à valorização do presente. Diferente de trackers tradicionais ou diários clássicos, o Daylyou ajuda os utilizadores a sair do modo automático, ganhar consciência do tempo vivido e construir memória pessoal com significado.

### Filosofia

> O Daylyou não mede performance.  
> O Daylyou preserva presença.

A aplicação convida o utilizador a:
- **Registar o dia** de forma estruturada, sem fricção
- **Capturar momentos significativos** enquanto acontecem
- **Ser convidado** (não forçado) a viver pelo menos 1 momento consciente por dia
- **Construir uma linha de memória visual, emocional e revisível** ao longo do tempo

### Princípios Fundamentais

- ❌ Não julga, não compara, não otimiza performance
- ✅ Valoriza presença e momentos significativos
- ✅ Zero culpa, zero comparação
- ✅ Sensação de coleção pessoal

---

## 🎯 Três Pilares Fundamentais

### 1. Daily Cards (Registo Diário)
Sistema de **Daily Cards** que permite registar, avaliar e documentar diversos aspetos da vida quotidiana.

**Sistema de Frente/Verso:**
- **Frente**: Resumo visual do dia (interface compacta e gráfica)
- **Verso**: Resumo detalhado e estatístico (dados quantitativos e qualitativos)

**Áreas de registo:**
- Estado interno e emocional
- Sono e ritmo temporal
- Hábitos e comportamentos
- Vida social e interações
- Mídia consumida
- Refeições
- Contexto e ambiente
- Notas segmentadas (manhã/tarde/noite)

### 2. 8 Esferas do Dia (Sistema de Avaliação)
Sistema de avaliação holística baseado em **8 dimensões** (escala 1-9):

1. **Estado Interno** (`internalState`) - Energia, clareza mental, emocional
2. **Intenção e Direção** (`intentionDirection`) - Alinhamento com objetivos
3. **Tempo e Ritmo** (`timeRhythm`) - Ritmo do dia, gestão de tempo
4. **Contexto e Ambiente** (`contextEnvironment`) - Onde esteve, qualidade do ambiente
5. **Vida Social** (`socialLife`) - Qualidade das interações
6. **Ações e Comportamentos** (`actionsBehaviors`) - Hábitos, ações concretas
7. **Conteúdo e Estímulos** (`contentStimuli`) - Média, consumo de informação
8. **Significado e Marcas** (`meaningMarks`) - Momentos significativos

**Implementação:** Swipe Deck interativo para preenchimento rápido (3-4 minutos)

### 3. Daylyou Fragmentos (Momentos Micro)
Registos de **momentos específicos** da vida (granularidade micro vs. dia inteiro macro).

**8 Tipos de Fragmentos:**
- 🎭 **Social** - Eventos sociais, encontros
- 🎬 **Cultural** - Filmes, Séries, Livros, Podcasts, Músicas
- ⚽ **Desporto** - Atividades desportivas assistidas ou praticadas
- 🧠 **Intelectual** - Aprendizagens, frases marcantes
- 💼 **Trabalho** - Momentos profissionais significativos
- 🛍️ **Consumo** - Compras, produtos
- ❤️ **Emocional** - Momentos marcantes emocionalmente
- ✨ **Aleatório** - Outros momentos

**Componentes de um Fragmento:**
- Título e emoji obrigatórios
- Descrição e intensidade emocional (1-9)
- Contexto: localização, pessoas envolvidas, período do dia
- Marcas visuais: fotos, notas de voz, frase curta
- Badge "Destaque Canónico" (isHighlight) - momentos que definem a vida

---

## 🛠️ Stack Tecnológico

### Frontend
- **Framework**: React 19.2.0 + TypeScript 5.6.3
- **Build Tool**: Vite 7.1.9
- **Routing**: Wouter 3.3.5 (lightweight routing)
- **State Management**: Zustand 5.0.9 (com persistência local)
- **Queries**: TanStack Query 5.60.5
- **Forms**: React Hook Form 7.66.0 + Zod 3.25.76
- **Styling**: Tailwind CSS 4.1.14 + PostCSS
- **UI Components**: Radix UI (shadcn/ui patterns)
- **Animations**: Framer Motion 12.23.24
- **Charts**: Recharts 2.15.4
- **Date Utils**: date-fns 3.6.0
- **Icons**: Lucide React 0.545.0

### Backend
- **Runtime**: Node.js
- **Framework**: Express 4.21.2
- **Database**: PostgreSQL (via pg 8.16.3)
- **ORM**: Drizzle ORM 0.39.3
- **Schema Validation**: Drizzle Zod 0.7.0
- **Authentication**: Passport 0.7.0 + Passport Local 1.0.0
- **Session**: Express Session 1.18.1 + connect-pg-simple 10.0.0
- **WebSockets**: ws 8.18.0

### DevOps & Tools
- **Package Manager**: npm
- **Type Checking**: TypeScript
- **CSS Processing**: PostCSS + Autoprefixer
- **Build**: tsx 4.20.5 + esbuild 0.25.0

---

## 📁 Estrutura do Projeto

```
daylyou-mobile/
├── Daily-Journal-Mobile/
│   ├── client/                      # Frontend React
│   │   ├── public/                  # Assets estáticos
│   │   └── src/
│   │       ├── components/          # Componentes React
│   │       │   ├── daily/          # Componentes de Daily Cards
│   │       │   ├── fragments/      # Componentes de Fragmentos
│   │       │   ├── layout/         # Layout components
│   │       │   ├── swipe-deck/     # Swipe Deck (8 Esferas)
│   │       │   └── ui/             # UI primitives (shadcn/ui)
│   │       ├── hooks/              # Custom React hooks
│   │       ├── lib/                # Utilities e store
│   │       ├── pages/              # Page components
│   │       ├── App.tsx             # Root component + Router
│   │       ├── index.css           # Global styles
│   │       └── main.tsx            # Entry point
│   ├── server/                     # Backend Express
│   │   ├── index.ts                # Server entry point
│   │   ├── routes.ts               # API routes
│   │   ├── static.ts               # Static file serving
│   │   ├── storage.ts              # Database interface
│   │   └── vite.ts                 # Vite dev server integration
│   ├── shared/                     # Shared code
│   │   └── schema.ts               # Database schema (Drizzle)
│   ├── script/                     # Build scripts
│   │   └── build.ts
│   ├── dist/                       # Build output
│   ├── package.json
│   ├── tsconfig.json
│   ├── vite.config.ts
│   ├── drizzle.config.ts
│   ├── postcss.config.js
│   └── components.json             # shadcn/ui config
├── PRD_DAYLYOU.md                  # Product Requirements Document
├── technical_brief.md              # Brief técnico
├── design_ux.md                    # Design & UX guidelines
└── README.md                       # Este arquivo
```

---

## 🚀 Como Começar

### Pré-requisitos
- Node.js (versão 18 ou superior)
- npm ou yarn
- PostgreSQL (para desenvolvimento local)

### Instalação

```bash
# Clone o repositório
git clone <repository-url>
cd daylyou-mobile/Daily-Journal-Mobile

# Instale as dependências
npm install
```

### Configuração do Banco de Dados

1. Configure uma base de dados PostgreSQL
2. Configure as variáveis de ambiente (se necessário)
3. Execute as migrações:

```bash
npm run db:push
```

### Desenvolvimento

```bash
# Inicia servidor de desenvolvimento (frontend + backend)
npm run dev

# Apenas frontend (porta 5000)
npm run dev:client
```

### Build para Produção

```bash
# Build completo (cliente + servidor)
npm run build

# Inicia em modo produção
npm start
```

### Type Checking

```bash
npm run check
```

---

## 🗺️ Rotas da Aplicação

```
/                    → Home (Dashboard principal)
/onboarding          → Onboarding (setup inicial)
/history             → History (calendário de dias)
/fragments           → Fragments (galeria de momentos)
/insights            → Insights (estatísticas)
/settings            → Settings (configurações)
/day/:date           → PostalView (vista detalhada do dia)
/fill/:date          → SwipeView (preencher 8 esferas)
```

---

## 🎨 Conceitos-Chave

### Metáfora Visual: Arquivo de Vida em Pedra

O Daylyou é apresentado como um arquivo pessoal durável:
- 📄 **Dia** → Folha
- 📚 **Mês** → Capítulo
- 🗂️ **Ano** → Dossiê

A sensação a transmitir é de permanência, cuidado, intenção e valor histórico.

### Gestos Principais

- **Swipe horizontal** → Navegação temporal (Ontem ← Hoje → Amanhã)
- **Tap** → Virar folha (frente ↔ verso)
- **Long press** → Menu de Edição

### Daily Card vs Fragmento

- **Daily Card**: Visão macro, simbólica e analítica de um dia inteiro
- **Fragmento**: Episódios micro que dão alma e identidade à memória

Um Daily Card pode existir sem Fragmentos, mas um Fragmento sempre pertence a um dia específico.

---

## 📊 Estado Atual do Projeto

### ✅ Implementado
- Sistema de 8 Esferas
- Swipe Deck para preenchimento
- Sistema de Fragmentos (8 tipos)
- Destaques Canónicos
- Persistência local (Zustand)
- UI components completa (shadcn/ui)
- Rotas principais
- Home dashboard
- Página de fragmentos
- Postal View (vista detalhada do dia)
- Onboarding

### ⚠️ Em Desenvolvimento
- Backend API (routes.ts ainda minimal)
- Sincronização com servidor
- Autenticação (schema existe, implementação parcial)
- Página de Insights (estatísticas)
- Página de History (calendário)
- Upload de fotos real (atualmente mockado)
- Notas de voz

### 📋 Planeado
- Notificações push
- Export de dados (PDF, JSON)
- Partilha de fragmentos
- Insights avançados (ML/análise de padrões)
- Widget de quick logging
- Integração com wearables (sleep tracking)

---

## 📚 Documentação Adicional

O projeto inclui documentação detalhada em:

- **PRD_DAYLYOU.md** - Product Requirements Document com visão completa do produto
- **technical_brief.md** - Decisões técnicas e arquitetura
- **design_ux.md** - Guidelines de design e experiência do utilizador
- **Claude.md** - Documentação técnica detalhada (legado)

---

## 🧩 Componentes Principais

### Daily Cards
Localização: `client/src/components/daily/`

- `BentoGrid.tsx` - Layout em grid para cards do dia
- `SpheresChart.tsx` - Radar chart das 8 esferas (Recharts)
- `SleepCard.tsx` - Card de sono
- `HabitCard.tsx` - Lista de hábitos completados
- `MealCard.tsx` - Refeições do dia
- `SocialCard.tsx` - Interações sociais
- `MediaCard.tsx` - Média consumida
- `FragmentCard.tsx` - Card de fragmento individual
- `PhotoGallery.tsx` - Galeria de até 9 fotos
- `NotesCard.tsx` - Notas segmentadas

### Fragments
Localização: `client/src/components/fragments/`

- `CategorySelector.tsx` - Drawer de seleção de tipo
- `TypedFragmentForm.tsx` - Formulário dinâmico por tipo

### Swipe Deck
Localização: `client/src/components/swipe-deck/`

- `SwipeDeck.tsx` - Container do swipe deck
- `SphereCard.tsx` - Card individual de esfera

---

## 🔧 Convenções de Código

### Nomenclatura
- **Componentes**: PascalCase (ex: `SphereCard.tsx`)
- **Hooks**: camelCase prefixado com `use` (ex: `useStore.ts`)
- **Utils/Libs**: camelCase (ex: `queryClient.ts`)
- **Tipos**: PascalCase (ex: `DailyLog`, `FragmentType`)
- **Constantes**: UPPER_SNAKE_CASE (ex: `DEFAULT_HABITS`)

### Imports com Alias
```typescript
@/components    → client/src/components
@/hooks         → client/src/hooks
@/lib           → client/src/lib
@/pages         → client/src/pages
```

---

## 🤝 Contribuição

### Prioridades Atuais
1. Completar backend API (CRUD de logs e fragmentos)
2. Implementar autenticação real
3. Página de Insights com gráficos e estatísticas
4. Página de History com calendário interativo
5. Upload de fotos real (storage)
6. Sincronização cliente-servidor
7. Testes unitários e E2E

### Áreas de Melhoria
- Performance de listas longas (virtualização)
- Acessibilidade (ARIA, screen readers)
- PWA offline-first
- Export de dados
- Internacionalização (i18n)

---

## 📄 Licença

MIT License

---

## 🙏 Agradecimentos

Este projeto é desenvolvido como uma aplicação pessoal de auto-conhecimento. Inspirado na necessidade de criar memória pessoal significativa e valorizar o presente.

---

**Última atualização**: 2025-01-13  
**Versão**: 1.0.0
