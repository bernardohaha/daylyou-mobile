# Daylyou Mobile - Documentação do Projeto

## Visão Geral

**Daylyou** é uma aplicação mobile progressiva (PWA) dedicada ao **auto-conhecimento**, **registo visual e estatístico da vida** e à **valorização do presente**. A aplicação permite aos utilizadores compreenderem-se melhor através de registos diários estruturados e momentos significativos capturados ao longo do tempo.

### Missão
Ajudar o utilizador a:
- Compreender-se a si mesmo de forma profunda
- Deixar um registo visual e estatístico da sua vida
- Sentir que está a viver e a valorizar o presente

---

## Três Pilares Fundamentais

### 1. Daily Logging (Registo Diário)
Sistema de **Daily Cards** que permite registar, avaliar e documentar diversos aspetos da vida quotidiana:

**Daily Cards - Sistema de Frente/Verso:**
- **Frente**: Resumo visual do dia (interface compacta e gráfica)
- **Verso**: Resumo detalhado e estatístico (dados quantitativos e qualitativos)

**Áreas de registo:**
- Atividades do cotidiano
- Nível social e interações
- Hábitos e comportamentos
- Mídia consumida
- Estado interno e emocional
- Sono e ritmo temporal
- Contexto e ambiente

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

### 3. Daily Fragments (Momentos Micro)
Registos de **momentos específicos** da vida (granularidade micro vs. dia inteiro macro):

**Tipos de Fragmentos:**
- **Social** 🎭 - Eventos sociais, encontros
- **Cultural** 🎬 - Cinema, teatro, exposições
- **Desporto** ⚽ - Atividades desportivas
- **Intelectual** 🧠 - Leitura, podcasts, cursos
- **Trabalho** 💼 - Momentos profissionais significativos
- **Consumo** 🛍️ - Compras, produtos
- **Emocional** ❤️ - Momentos marcantes emocionalmente
- **Aleatório** ✨ - Outros momentos

**Componentes de um Fragmento:**
- Título e emoji obrigatórios
- Descrição
- Intensidade emocional (1-9)
- Contexto: localização, pessoas envolvidas, período do dia
- Marcas visuais: fotos, notas de voz, frase curta
- Badge "Destaque Canónico" (isHighlight) - momentos que definem a vida

---

## Stack Tecnológico

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

## Estrutura do Projeto

```
daylyou-mobile/
├── Daily-Journal-Mobile/
│   ├── client/                      # Frontend React
│   │   ├── public/                  # Assets estáticos
│   │   └── src/
│   │       ├── components/          # Componentes React
│   │       │   ├── daily/          # Componentes de Daily Cards
│   │       │   │   ├── BentoGrid.tsx
│   │       │   │   ├── DatePickerDrawer.tsx
│   │       │   │   ├── EditCompleteLogDialog.tsx
│   │       │   │   ├── FragmentCard.tsx
│   │       │   │   ├── HabitCard.tsx
│   │       │   │   ├── MealCard.tsx
│   │       │   │   ├── MediaCard.tsx
│   │       │   │   ├── NotesCard.tsx
│   │       │   │   ├── PhotoGallery.tsx
│   │       │   │   ├── RadarInput.tsx
│   │       │   │   ├── SleepCard.tsx
│   │       │   │   ├── SocialCard.tsx
│   │       │   │   └── SpheresChart.tsx
│   │       │   ├── fragments/       # Componentes de Fragmentos
│   │       │   │   ├── CategorySelector.tsx
│   │       │   │   └── TypedFragmentForm.tsx
│   │       │   ├── layout/          # Layout components
│   │       │   │   └── MobileShell.tsx
│   │       │   ├── swipe-deck/      # Swipe Deck (8 Esferas)
│   │       │   │   ├── SphereCard.tsx
│   │       │   │   └── SwipeDeck.tsx
│   │       │   └── ui/              # UI primitives (shadcn/ui)
│   │       ├── hooks/               # Custom React hooks
│   │       ├── lib/                 # Utilities
│   │       │   ├── hooks.ts
│   │       │   ├── queryClient.ts
│   │       │   ├── store.ts         # Zustand store (CORE)
│   │       │   └── utils.ts
│   │       ├── pages/               # Page components
│   │       │   ├── Fragments.tsx    # Página de Fragmentos
│   │       │   ├── History.tsx      # Histórico de dias
│   │       │   ├── Home.tsx         # Dashboard principal
│   │       │   ├── Insights.tsx     # Estatísticas e insights
│   │       │   ├── not-found.tsx
│   │       │   ├── Onboarding.tsx   # Setup inicial
│   │       │   ├── PostalView.tsx   # Vista detalhada do dia
│   │       │   ├── Settings.tsx     # Configurações
│   │       │   └── SwipeView.tsx    # Swipe Deck view
│   │       ├── App.tsx              # Root component + Router
│   │       ├── index.css            # Global styles
│   │       └── main.tsx             # Entry point
│   ├── server/                      # Backend Express
│   │   ├── index.ts                 # Server entry point
│   │   ├── routes.ts                # API routes (minimal atm)
│   │   ├── static.ts                # Static file serving
│   │   ├── storage.ts               # Database interface
│   │   └── vite.ts                  # Vite dev server integration
│   ├── shared/                      # Shared code
│   │   └── schema.ts                # Database schema (Drizzle)
│   ├── script/                      # Build scripts
│   │   └── build.ts
│   ├── dist/                        # Build output
│   ├── package.json
│   ├── tsconfig.json
│   ├── vite.config.ts
│   ├── drizzle.config.ts
│   ├── postcss.config.js
│   └── components.json              # shadcn/ui config
```

---

## Arquitetura de Dados

### Estado Global (Zustand Store)
Localização: `client/src/lib/store.ts`

**Principais Tipos:**

```typescript
// Log diário completo
DailyLog {
  id: string;                    // YYYY-MM-DD
  date: string;
  dayType: 'work' | 'off' | 'vacation';

  // Sono
  sleep: {
    bedTime: string;
    wakeTime: string;
    hours: number;
    quality: number;             // 1-9
    wokeUpEarly: boolean;
  };

  // 8 Esferas
  spheres: DaySpheres;           // 8 valores 1-9
  spheresCompletion: { ... };    // tracking de preenchimento

  // Cards
  habitsCompleted: string[];
  meals: MealLog[];
  social: SocialLog[];
  media: MediaLog[];
  fragments: FragmentLog[];      // Fragmentos do dia

  // Notas segmentadas por período
  notes: {
    morning: string;
    afternoon: string;
    night: string;
    ratings: { morning: number; afternoon: number; night: number };
  };

  // Visual
  photos: string[];              // max 9, base64
  highlightFragmentId?: string;  // Destaque do dia

  // Métricas
  finalScore: number;            // média das 8 esferas
  isComplete: boolean;
}

// Fragmento de vida
FragmentLog {
  id: string;
  title: string;
  description: string;
  type: FragmentType;            // social, cultural, sports, etc.
  emoji: string;                 // obrigatório
  emotionIntensity?: number;     // 1-9

  // Contexto
  location?: string;
  peopleInvolved?: string[];
  timeOfDay?: 'morning' | 'afternoon' | 'night';

  // Conteúdo
  linkedMedia?: { type, title };
  photos?: string[];
  voiceNote?: string;
  shortPhrase?: string;          // frase de até 3 linhas

  // Badge
  isHighlight: boolean;          // Destaque canónico

  timestamp?: string;
  createdAt: string;
}

// 8 Esferas
DaySpheres {
  internalState: number;         // 1-9
  intentionDirection: number;
  timeRhythm: number;
  contextEnvironment: number;
  socialLife: number;
  actionsBehaviors: number;
  contentStimuli: number;
  meaningMarks: number;
}
```

### Persistência
- **Cliente**: localStorage via Zustand persist middleware
- **Servidor**: PostgreSQL (schema em `shared/schema.ts`)
- **Migração**: Funções automáticas para compatibilidade (radar → spheres, category → type)

---

## Rotas da Aplicação

```
/                    → Home (Dashboard principal)
/onboarding          → Onboarding (setup inicial)
/history             → History (calendário de dias)
/fragments           → Fragments (galeria de momentos)
/insights            → Insights (estatísticas)
/settings            → Settings (configurações)
/day/:date           → PostalView (vista detalhada dia)
/fill/:date          → SwipeView (preencher 8 esferas)
```

---

## Fluxos Principais

### 1. Fluxo de Primeiro Uso
1. Utilizador acede à aplicação
2. Redirecionado para `/onboarding`
3. Define configurações iniciais (wake goal, hábitos)
4. Estado `isOnboarded` = true
5. Redirecionado para `/` (Home)

### 2. Fluxo de Preenchimento do Dia
**Home (`/`) → Swipe Deck:**
1. Utilizador clica "Preencher Dia"
2. Swipe Deck apresenta 8 cards (esferas)
3. Para cada esfera: escala 1-9 + pergunta contextual
4. Auto-save em `spheresCompletion`
5. Ao concluir: calcula `finalScore`, marca `isComplete`
6. Toast de confirmação + volta ao Home

**Home (`/`) → Ver Folha Postal:**
1. Disponível após esferas preenchidas
2. Navega para `/day/:date` (PostalView)
3. Vista completa: gráficos, cards, fragmentos, fotos
4. Modo de "postal" do dia

### 3. Fluxo de Criação de Fragmento
**Fragments (`/fragments`) → Criar Fragmento:**
1. FAB (Floating Action Button) "+"
2. Category Selector (drawer com 8 tipos)
3. Seleciona tipo → abre TypedFragmentForm
4. Formulário adaptado ao tipo selecionado
5. Campos: título, emoji, descrição, intensidade, contexto, fotos
6. Submit → adiciona ao dia atual (`logs[today].fragments`)
7. Fragmento aparece na feed

### 4. Fluxo de Destaques Canónicos
- Utilizador marca fragmento como `isHighlight = true`
- Aparece com badge ⭐ em todas as vistas
- Secção especial "Destaques Canónicos" em `/fragments`
- Pode definir um fragmento como `highlightFragmentId` do dia

---

## Funcionalidades-Chave

### 1. Swipe Deck (8 Esferas)
**Componente:** `client/src/components/swipe-deck/SwipeDeck.tsx`

- Interface de swipe estilo "stories"
- 8 cards sequenciais, um por esfera
- Inputs tipo radar/slider (1-9)
- Tracking de progresso (X/8)
- Permite voltar atrás
- Guarda estado parcial

### 2. Postal View (Vista do Dia)
**Página:** `client/src/pages/PostalView.tsx`

**Secções:**
- Header: data, tipo de dia, score final
- Gráfico de radar das 8 esferas (SpheresChart)
- Cards visuais: Sleep, Habits, Meals, Social, Media
- Fragmentos do dia (se existirem)
- Galeria de fotos (PhotoGallery)
- Notas segmentadas (manhã/tarde/noite)

### 3. Feed de Fragmentos
**Página:** `client/src/pages/Fragments.tsx`

**Features:**
- Listagem cronológica de todos os fragmentos
- Filtros por tipo (8 categorias)
- Secção de "Destaques Canónicos"
- Cards com foto de capa (se disponível)
- Modal de detalhe ao clicar
- Badges de tipo, intensidade emocional
- Metadados: localização, pessoas, timestamp

### 4. Histórico de Dias
**Página:** `client/src/pages/History.tsx`

- Calendário de dias registados
- Indicadores visuais de completude
- Navegação rápida para dias específicos
- Insights mensais/semanais

### 5. Dashboard (Home)
**Página:** `client/src/pages/Home.tsx`

**Widgets:**
- Card principal: Estado das 8 esferas (vazio/parcial/completo)
- Barra de progresso (X/8 esferas)
- Tipo de dia (work/off/vacation)
- Quick actions: criar fragmento, ver postal
- Fragmentos de hoje (listagem compacta)

---

## Componentes Principais

### Daily Cards
Localização: `client/src/components/daily/`

- **BentoGrid.tsx**: Layout em grid para cards do dia
- **SpheresChart.tsx**: Radar chart das 8 esferas (Recharts)
- **SleepCard.tsx**: Card de sono (horas, qualidade)
- **HabitCard.tsx**: Lista de hábitos completados
- **MealCard.tsx**: Refeições do dia
- **SocialCard.tsx**: Interações sociais
- **MediaCard.tsx**: Média consumida
- **FragmentCard.tsx**: Card de fragmento individual
- **PhotoGallery.tsx**: Galeria de até 9 fotos
- **NotesCard.tsx**: Notas segmentadas (manhã/tarde/noite)
- **RadarInput.tsx**: Input para valores de radar/esferas
- **DatePickerDrawer.tsx**: Seletor de data
- **EditCompleteLogDialog.tsx**: Modal de edição de dia completo

### Fragments
Localização: `client/src/components/fragments/`

- **CategorySelector.tsx**: Drawer de seleção de tipo de fragmento
- **TypedFragmentForm.tsx**: Formulário dinâmico por tipo

### Swipe Deck
Localização: `client/src/components/swipe-deck/`

- **SwipeDeck.tsx**: Container do swipe deck
- **SphereCard.tsx**: Card individual de esfera

### UI Primitives
Localização: `client/src/components/ui/`

Componentes baseados em shadcn/ui (Radix UI + Tailwind):
- Accordion, Alert, Avatar, Badge, Button, Calendar, Card
- Checkbox, Collapsible, Command, ContextMenu, Dialog, Drawer
- Dropdown, Empty, Field, Form, HoverCard, Input, Label
- Menubar, NavigationMenu, Pagination, Popover, Progress
- RadioGroup, ScrollArea, Select, Separator, Sheet, Sidebar
- Skeleton, Slider, Sonner, Spinner, Switch, Table, Tabs
- Textarea, Toast, Toggle, Tooltip
- **HighlightBadge.tsx**: Badge customizado para destaques

### Layout
Localização: `client/src/components/layout/`

- **MobileShell.tsx**: Container principal com navegação bottom tab

---

## Conceitos-Chave de UX

### 1. Filosofia de Registo
- **Macro (dia inteiro)**: 8 Esferas, cards de atividades
- **Micro (momentos)**: Fragmentos de vida
- **Visual + Quantitativo**: Fotos + scores numéricos
- **Reflexão estruturada**: Perguntas guiadas vs. diário livre

### 2. Gamificação Suave
- Score final do dia (média das 8 esferas)
- Progresso visual (X/8 esferas completas)
- Badges de destaque (⭐ canónico)
- Hábitos completados

### 3. Design Mobile-First
- Interface tipo "stories" (swipe deck)
- FAB para ações rápidas
- Drawers/sheets para formulários
- Bottom navigation
- Otimização para uso com uma mão

### 4. Valorização do Presente
- Foco no "hoje" (home page)
- Criação rápida de fragmentos (3 taps)
- Notificações para lembrar de registar o dia
- Reflexão end-of-day (3-4 minutos)

---

## Personalização e Configurações

**Settings (`/settings`):**
- Wake goal (hora de acordar ideal)
- Hábitos personalizados (label + emoji)
- Parâmetros de radar (legacy, migrado para esferas)
- Tema (dark/light)
- Notificações

---

## Estado Atual do Projeto

### Implementado
- ✅ Sistema de 8 Esferas
- ✅ Swipe Deck para preenchimento
- ✅ Sistema de Fragmentos (8 tipos)
- ✅ Destaques Canónicos
- ✅ Persistência local (Zustand)
- ✅ UI components completa (shadcn/ui)
- ✅ Rotas principais
- ✅ Home dashboard
- ✅ Página de fragmentos
- ✅ Postal View
- ✅ Onboarding

### Em Desenvolvimento
- ⚠️ Backend API (routes.ts ainda minimal)
- ⚠️ Sincronização com servidor
- ⚠️ Autenticação (schema existe, implementação parcial)
- ⚠️ Página de Insights (estatísticas)
- ⚠️ Página de History (calendário)
- ⚠️ Upload de fotos real (atualmente mockado)
- ⚠️ Notas de voz

### Planeado
- 📋 Notificações push
- 📋 Export de dados (PDF, JSON)
- 📋 Partilha de fragmentos
- 📋 Insights avançados (ML/análise de padrões)
- 📋 Widget de quick logging
- 📋 Integração com wearables (sleep tracking)

---

## Como Trabalhar no Projeto

### Instalação
```bash
cd Daily-Journal-Mobile
npm install
```

### Desenvolvimento
```bash
npm run dev          # Inicia dev server (Vite + Express)
npm run dev:client   # Apenas frontend (porta 5000)
```

### Build
```bash
npm run build        # Build completo (cliente + servidor)
npm start            # Produção
```

### Database
```bash
npm run db:push      # Push schema para PostgreSQL (Drizzle)
```

### Type Checking
```bash
npm run check        # TypeScript check
```

---

## Convenções de Código

### Nomenclatura
- **Componentes**: PascalCase (ex: `SphereCard.tsx`)
- **Hooks**: camelCase prefixado com `use` (ex: `useStore.ts`)
- **Utils/Libs**: camelCase (ex: `queryClient.ts`)
- **Tipos**: PascalCase (ex: `DailyLog`, `FragmentType`)
- **Constantes**: UPPER_SNAKE_CASE (ex: `DEFAULT_HABITS`)

### Estrutura de Componentes
```typescript
// 1. Imports
import React from 'react';
import { Component } from '@/components/ui/component';

// 2. Types/Interfaces
type Props = { ... };

// 3. Component
export default function ComponentName({ props }: Props) {
  // 3a. Hooks
  const store = useStore();
  const [state, setState] = useState();

  // 3b. Handlers
  const handleClick = () => { ... };

  // 3c. Effects
  useEffect(() => { ... }, [deps]);

  // 3d. Render
  return ( ... );
}
```

### Imports com Alias
```typescript
@/components    → client/src/components
@/hooks         → client/src/hooks
@/lib           → client/src/lib
@/pages         → client/src/pages
```

---

## Princípios de Design

### 1. Minimalismo Contemplativo
- Espaço em branco generoso
- Tipografia clara e hierarquizada
- Cores suaves com acentos intencionais
- Animações subtis (`transition-contemplative`)

### 2. Visual Storytelling
- Uso abundante de emojis (identidade, rapidez)
- Fotografias como elemento central
- Gráficos de radar (holístico, visual)
- Cards tipo "postal" (memória tangível)

### 3. Acessibilidade
- Contraste adequado (WCAG AA)
- Textos alternativos em imagens
- Navegação por teclado
- Estados de focus visíveis
- Dark mode

### 4. Performance
- Lazy loading de componentes
- Virtualização de listas longas (se necessário)
- Imagens otimizadas
- Bundle splitting
- PWA (offline-first)

---

## Glossário

- **Daily Card**: Card de registo de uma área da vida (ex: Sleep Card, Meal Card)
- **Esfera**: Uma das 8 dimensões de avaliação do dia (1-9)
- **Fragmento**: Momento específico da vida registado (micro vs. dia = macro)
- **Destaque Canónico**: Fragmento marcado como momento-chave que define a vida
- **Postal View**: Vista completa e detalhada de um dia específico
- **Swipe Deck**: Interface de swipe para preenchimento das 8 esferas
- **Score Final**: Média das 8 esferas do dia
- **Tipo de Dia**: work, off, vacation

---

## Recursos Úteis

### Design System
- **shadcn/ui**: https://ui.shadcn.com/
- **Radix UI**: https://www.radix-ui.com/
- **Tailwind CSS**: https://tailwindcss.com/

### Bibliotecas
- **Zustand**: https://zustand-demo.pmnd.rs/
- **TanStack Query**: https://tanstack.com/query/latest
- **React Hook Form**: https://react-hook-form.com/
- **Zod**: https://zod.dev/
- **Recharts**: https://recharts.org/
- **date-fns**: https://date-fns.org/

### Backend
- **Drizzle ORM**: https://orm.drizzle.team/
- **Express**: https://expressjs.com/
- **Passport**: https://www.passportjs.org/

---

## Contribuição

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

## Contacto e Suporte

Este projeto é desenvolvido como uma aplicação pessoal de auto-conhecimento. Para questões técnicas ou sugestões, consulte o repositório do código.

---

**Última atualização**: 2025-12-31
**Versão**: 1.0.0
