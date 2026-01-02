# Daylyou Mobile - Documentação Técnica do Projeto

## Visão Geral

**Daylyou** é uma aplicação mobile progressiva (PWA) dedicada ao **auto-conhecimento**, **registo visual e estatístico da vida** e à **valorização do presente**. A aplicação permite aos utilizadores compreenderem-se melhor através de registos diários estruturados e momentos significativos capturados ao longo do tempo.

### Missão
Ajudar o utilizador a:
- Compreender-se a si mesmo de forma profunda
- Deixar um registo visual e estatístico da sua vida
- Sentir que está a viver e a valorizar o presente

---

## Dois Pilares Fundamentais

### 1. Card-Based Daily Logging (Registo Diário por Cards)

Sistema de **Daily Cards** que permite registar, avaliar e documentar diversos aspetos da vida quotidiana através de um **fluxo cronológico estruturado**.

#### Sistema de Cards: 9 Obrigatórios + 7 Opcionais

**9 Cards Obrigatórios** (sequência cronológica fixa):

1. **Sleep Card** 🌙
   - Hora de deitar (`bedTime`)
   - Hora de acordar (`wakeTime`)
   - Horas totais de sono (`hours`)
   - Qualidade do sono (1-9)
   - Acordou cedo? (`wokeUpEarly: boolean`)

2. **Context Card** 📍
   - Tags do dia (multi-select): `work`, `off`, `vacation`, `social-event`, `family`, `friends`
   - Localizações visitadas (opcional)
   - Pessoas envolvidas (opcional)

3. **Morning Period Card** 🌅
   - Eventos da manhã (`events: string`)
   - Reflexões da manhã (`reflections: string`)

4. **Lunch Meal Card** 🍽️
   - Tipo de comida (`foodType: string[]` multi-select)
   - Bebidas (`drinks?: string`)
   - Com quem (`withWho?: string`)
   - Notas (`notes?: string`)

5. **Habits Card** ✓
   - Hábitos completados (`completed: string[]`)
   - Streaks automáticos (`streaks: Record<string, number>`)
   - Visualização de progresso

6. **Afternoon Period Card** 🌞
   - Eventos da tarde (`events: string`)
   - Reflexões da tarde (`reflections: string`)

7. **Dinner Meal Card** 🍽️
   - Tipo de comida (`foodType: string[]` multi-select)
   - Bebidas (`drinks?: string`)
   - Com quem (`withWho?: string`)
   - Notas (`notes?: string`)

8. **Night Period Card** 🌃
   - Resumo do dia (`summary: string`)
   - Reflexão final (`finalReflection: string`)
   - Fotos do dia (até 9, base64)

9. **Evaluation Card** ⭐
   - Avaliação geral do dia (1-9)
   - Selo "Perfect Day" (quando rating = 9)
   - Sentiment tags (multi-select chips)
   - Destaque do dia (`dayHighlight`: emoji + 200 chars)

**7 Cards Opcionais** (adicionados dinamicamente):

1. **Weather Card** 🌤️
   - Condições meteorológicas
   - Temperatura
   - Notas

2. **PC Activities Card** 💻
   - Horas no computador
   - Tipos de atividade: Trabalho, Estudo, Gaming, Streaming, Entretenimento, Social, Criatividade
   - Programas utilizados
   - Jogos jogados (se Gaming selecionado)

3. **Gym Card** 💪
   - Tipo de treino: Musculação, Cardio, Funcional, Yoga, etc.
   - Grupos musculares: Bicep, Peito, Tricep, Ombros, Pernas, Costas, Cardio, Antebraço
   - Duração
   - Intensidade (1-5)
   - Lista de exercícios

4. **Detailed Media Card** 🎬
   - Múltiplos itens: Filme, Série, Livro, Podcast, Documentário, Artigo, Música/Álbum
   - Rating (1-5 estrelas)
   - Badge "Favorite" (selo Daylyou)
   - Título, comentário

5. **Finances Card** 💰
   - Transações (Despesa/Receita)
   - Categorias diferentes por tipo
   - Valor em euros
   - Descrição

6. **Learnings Card** 📚
   - Múltiplos items de aprendizagem
   - Fonte: Livro, Conversa, Podcast, Vídeo, Experiência
   - Descrição (300 chars max)
   - Emoji

7. **Special Meal Card** 🍴
   - Restaurante
   - Prato
   - Rating (1-5)
   - Com quem
   - Fotos

#### Card Registry System

**Localização**: `client/src/lib/cardRegistry.ts`

Sistema centralizado que gere:
- Configuração de todos os cards (mandatory + optional)
- Ordem cronológica de apresentação
- Lógica de completude de cada card
- Sugestões automáticas (ex: Gym card quando habit "Exercício" marcado)
- Identificação e metadados de cada card

**Estrutura**:
```typescript
interface CardConfig {
  id: string;
  title: string;
  icon: LucideIcon;
  type: 'mandatory' | 'optional';
  category?: 'period' | 'meal' | 'activity' | 'wellness' | 'productivity' | 'finance' | 'learning';
  description: string;
  checkCompletion: (log: DailyLog) => boolean;
}
```

### 2. Daily Fragments (Momentos Micro)

Registos de **momentos específicos** da vida (granularidade micro vs. dia inteiro macro):

**Tipos de Fragmentos:**
- **Social** 🎭 - Eventos sociais, encontros
- **Cultural** 🎬 - Filmes, Séries, Livros, Podcasts, Músicas
- **Desporto** ⚽ - Atividades desportivas assistidas ou praticadas
- **Intelectual** 🧠 - Aprendizagens, frases marcantes
- **Trabalho** 💼 - Momentos profissionais significativos
- **Consumo** 🛍️ - Compras, produtos (com `price` e `rating`)
- **Emocional** ❤️ - Momentos marcantes emocionalmente
- **Aleatório** ✨ - Outros momentos

**Configuração de Fragmentos**: `client/src/lib/fragmentTypeConfig.ts`

**Componentes de um Fragmento:**
- Título e emoji obrigatórios
- Descrição
- Intensidade emocional (1-9)
- Contexto: localização, pessoas envolvidas, período do dia
- Marcas visuais: fotos, notas de voz, frase curta
- Badge "Destaque Canónico" (`isHighlight`) - momentos que definem a vida
- Campos específicos por tipo (configuráveis)

---

## Stack Tecnológico

### Frontend
- **Framework**: React 19.2.0 + TypeScript 5.6.3
- **Build Tool**: Vite 7.1.9
- **Routing**: Wouter 3.3.5 (lightweight routing)
- **State Management**: Zustand 5.0.9 (com persistência localStorage)
- **Forms**: React Hook Form 7.66.0 + Zod 3.25.76
- **Styling**: Tailwind CSS 4.1.14 + PostCSS
- **UI Components**: Radix UI (shadcn/ui patterns)
- **Animations**: Framer Motion 12.23.24
- **Charts**: Recharts 2.15.4
- **Date Utils**: date-fns 3.6.0
- **Icons**: Lucide React 0.545.0

### Backend (Planeado)
- **Runtime**: Node.js
- **Framework**: Express 4.21.2
- **Database**: PostgreSQL (via pg 8.16.3)
- **ORM**: Drizzle ORM 0.39.3
- **Schema Validation**: Drizzle Zod 0.7.0

**Nota**: Backend API existe mas **NÃO está integrado**. Atualmente a aplicação funciona totalmente em modo **local-first** com localStorage.

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
│   ├── client/                          # Frontend React
│   │   ├── public/                      # Assets estáticos
│   │   └── src/
│   │       ├── components/              # Componentes React
│   │       │   ├── daily/              # Componentes de Daily Cards (24 cards)
│   │       │   │   ├── SleepCard.tsx
│   │       │   │   ├── ContextCard.tsx
│   │       │   │   ├── MorningPeriodCard.tsx
│   │       │   │   ├── LunchMealCard.tsx
│   │       │   │   ├── HabitCard.tsx
│   │       │   │   ├── AfternoonPeriodCard.tsx
│   │       │   │   ├── DinnerMealCard.tsx
│   │       │   │   ├── NightPeriodCard.tsx
│   │       │   │   ├── EvaluationCard.tsx
│   │       │   │   ├── WeatherCard.tsx
│   │       │   │   ├── PcActivitiesCard.tsx
│   │       │   │   ├── GymCard.tsx
│   │       │   │   ├── DetailedMediaCard.tsx
│   │       │   │   ├── FinancesCard.tsx
│   │       │   │   ├── LearningsCard.tsx
│   │       │   │   ├── SpecialMealCard.tsx
│   │       │   │   ├── BentoGrid.tsx
│   │       │   │   ├── DatePickerDrawer.tsx
│   │       │   │   ├── EditCompleteLogDialog.tsx
│   │       │   │   ├── FragmentCard.tsx
│   │       │   │   ├── PhotoGallery.tsx
│   │       │   │   ├── DailyTimeline.tsx
│   │       │   │   └── OptionalCardSelector.tsx
│   │       │   ├── fragments/           # Componentes de Fragmentos
│   │       │   │   ├── CategorySelector.tsx
│   │       │   │   └── TypedFragmentForm.tsx
│   │       │   ├── layout/              # Layout components
│   │       │   │   └── MobileShell.tsx
│   │       │   ├── swipe-deck/          # Swipe Deck (Cards)
│   │       │   │   ├── SphereCard.tsx   (usado para cards cronológicos)
│   │       │   │   └── SwipeDeck.tsx
│   │       │   └── ui/                  # UI primitives (shadcn/ui)
│   │       │       └── (60+ components)
│   │       ├── hooks/                   # Custom React hooks
│   │       ├── lib/                     # Utilities
│   │       │   ├── cardRegistry.ts      # Card configuration system ⭐
│   │       │   ├── fragmentTypeConfig.ts # Fragment type configs ⭐
│   │       │   ├── hooks.ts
│   │       │   ├── queryClient.ts
│   │       │   ├── store.ts             # Zustand store (CORE) ⭐
│   │       │   └── utils.ts
│   │       ├── pages/                   # Page components
│   │       │   ├── Fragments.tsx        # Página de Fragmentos
│   │       │   ├── History.tsx          # Histórico de dias
│   │       │   ├── Home.tsx             # Dashboard principal
│   │       │   ├── Insights.tsx         # Estatísticas (placeholder)
│   │       │   ├── not-found.tsx
│   │       │   ├── Onboarding.tsx       # Setup inicial
│   │       │   ├── PostalView.tsx       # Vista detalhada do dia
│   │       │   ├── Settings.tsx         # Configurações
│   │       │   └── SwipeView.tsx        # Card filling view
│   │       ├── App.tsx                  # Root component + Router
│   │       ├── index.css                # Global styles
│   │       └── main.tsx                 # Entry point
│   ├── server/                          # Backend Express (não integrado)
│   │   ├── index.ts                     # Server entry point
│   │   ├── routes.ts                    # API routes (existem mas não usados)
│   │   ├── static.ts                    # Static file serving
│   │   ├── storage.ts                   # Database interface
│   │   └── vite.ts                      # Vite dev server integration
│   ├── shared/                          # Shared code
│   │   └── schema.ts                    # Database schema (desatualizado)
│   ├── script/                          # Build scripts
│   │   └── build.ts
│   ├── dist/                            # Build output
│   ├── package.json
│   ├── tsconfig.json
│   ├── vite.config.ts
│   ├── drizzle.config.ts
│   ├── postcss.config.js
│   └── components.json                  # shadcn/ui config
```

---

## Arquitetura de Dados

### Estado Global (Zustand Store)
**Localização**: `client/src/lib/store.ts`

**Principais Tipos:**

```typescript
// Log diário completo
interface DailyLog {
  id: string;                              // YYYY-MM-DD
  date: string;

  // Contexto do dia
  dayContext: {
    tags: string[];                        // work, off, vacation, social-event, family, friends
    locations?: string[];
    peopleInvolved?: string[];
  };

  // Sono
  sleep: {
    bedTime: string;
    wakeTime: string;
    hours: number;
    quality: number;                       // 1-9
    wokeUpEarly: boolean;
  };

  // Períodos do dia (NOVO)
  periods: {
    morning: {
      events: string;
      reflections: string;
    };
    afternoon: {
      events: string;
      reflections: string;
    };
    night: {
      summary: string;
      finalReflection: string;
    };
  };

  // Refeições (NOVA ESTRUTURA - objetos, não arrays)
  lunch: {
    foodType: string[];                    // multi-select
    drinks?: string;
    withWho?: string;
    notes?: string;
  };
  dinner: {
    foodType: string[];                    // multi-select
    drinks?: string;
    withWho?: string;
    notes?: string;
  };

  // Hábitos (COM STREAKS)
  habits: {
    completed: string[];                   // IDs dos hábitos completados hoje
    streaks: Record<string, number>;       // streak automático por hábito
  };

  // Avaliação do dia (SUBSTITUI finalScore)
  dayEvaluation: {
    overallRating: number;                 // 1-9
    isPerfectDay: boolean;                 // seal quando rating = 9
    sentimentTags: string[];               // chips de sentimento
    dayHighlight: string;                  // emoji + 200 chars max
  };

  // Optional Cards
  optionalCardsAdded: string[];            // IDs dos cards opcionais adicionados

  // Optional Card Data
  weather?: {
    conditions: string;
    temperature: string;
    notes: string;
  };

  pcActivities?: {
    hours: number;
    activityTypes: string[];               // Trabalho, Gaming, etc.
    programs: string;
    gamesPlayed?: string;
  };

  gym?: {
    workoutType: string[];
    muscleGroups: string[];                // 8 grupos
    duration: number;
    intensity: number;                     // 1-5
    exercises: string;
  };

  detailedMedia?: {
    items: Array<{
      id: string;
      type: string;                        // Filme, Série, Livro, etc.
      title: string;
      rating: number;                      // 1-5
      isFavorite: boolean;                 // badge
      comment?: string;
    }>;
  };

  finances?: {
    transactions: Array<{
      id: string;
      type: 'expense' | 'income';
      amount: number;
      category: string;
      description: string;
    }>;
  };

  learnings?: {
    items: Array<{
      id: string;
      learning: string;                    // 300 chars max
      source: string;                      // Livro, Conversa, Podcast, etc.
      emoji: string;
    }>;
  };

  specialMeal?: {
    restaurant: string;
    dish: string;
    rating: number;                        // 1-5
    withWho?: string;
    photos?: string[];
  };

  // Fragmentos do dia
  fragments: FragmentLog[];

  // Fotos
  photos: string[];                        // max 9, base64 (associadas a Night Card)

  // Metadata
  isComplete: boolean;
  createdAt: string;
  updatedAt: string;

  // LEGACY FIELDS (mantidos para compatibilidade)
  dayType?: 'work' | 'off' | 'vacation';  // deprecated, usar dayContext.tags
  spheres?: any;                           // deprecated
  spheresCompletion?: any;                 // deprecated
  radar?: any;                             // deprecated
}

// Fragmento de vida
interface FragmentLog {
  id: string;
  title: string;
  description: string;
  type: FragmentType;                      // social, cultural, sports, etc.
  emoji: string;                           // obrigatório
  emotionIntensity?: number;               // 1-9

  // Contexto
  location?: string;
  peopleInvolved?: string[];
  timeOfDay?: 'morning' | 'afternoon' | 'night';

  // Conteúdo específico por tipo
  linkedMedia?: { type: string; title: string };
  price?: number;                          // para consumption type
  rating?: number;                         // para consumption type
  sportType?: string;                      // para sports type
  photos?: string[];
  voiceNote?: string;
  shortPhrase?: string;                    // frase de até 3 linhas

  // Badge
  isHighlight: boolean;                    // Destaque canónico

  timestamp?: string;
  createdAt: string;
}

type FragmentType = 'social' | 'cultural' | 'sports' | 'intellectual' | 'work' | 'consumption' | 'emotional' | 'random';
```

### Persistência
- **Cliente**: localStorage via Zustand persist middleware
- **Servidor**: Não conectado (planeado: PostgreSQL com schema em `shared/schema.ts`)

### Migração de Dados Legados

O código mantém compatibilidade com versões anteriores através de:
- `migrateLegacyLog()` - converte estruturas antigas
- `normalizeLog()` - normaliza dados após load
- Campos legacy mantidos mas não utilizados

---

## Rotas da Aplicação

```
/                    → Home (Dashboard principal)
/onboarding          → Onboarding (setup inicial)
/history             → History (calendário de dias)
/fragments           → Fragments (galeria de momentos)
/insights            → Insights (estatísticas - placeholder)
/settings            → Settings (configurações)
/day/:date           → PostalView (vista detalhada do dia)
/fill/:date          → SwipeView (preencher cards cronológicos)
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
**Home (`/`) → Swipe Deck de Cards:**

1. Utilizador clica "Preencher Dia"
2. Swipe Deck apresenta sequência cronológica:
   - Sleep → Context → Morning → Lunch → Habits
   - → Afternoon → Dinner → Night → Evaluation
3. Utilizador pode adicionar optional cards durante o fluxo
4. Auto-save de cada card
5. Tracking de progresso (X/9 mandatory cards)
6. Sugestões automáticas (ex: Gym card se habit "Exercício" marcado)
7. Ao concluir: marca `isComplete = true`
8. Toast de confirmação + volta ao Home

**Inserção de Optional Cards:**
- Durante o fluxo, botão "+" permite adicionar optional cards
- Optional Card Selector abre com os 7 cards disponíveis
- Após seleção, card é inserido na sequência
- Tracking em `optionalCardsAdded[]`

**Home (`/`) → Ver Folha Postal:**
1. Disponível após cards preenchidos
2. Navega para `/day/:date` (PostalView)
3. Vista completa: frente/verso animado
4. Frente: resumo visual (Bento Grid)
5. Verso: timeline detalhado + fragmentos + fotos

### 3. Fluxo de Criação de Fragmento
**Fragments (`/fragments`) → Criar Fragmento:**

1. FAB (Floating Action Button) "+"
2. Category Selector (drawer com 8 tipos)
3. Seleciona tipo → abre TypedFragmentForm
4. Formulário adaptado ao tipo selecionado (via fragmentTypeConfig)
5. Campos: título, emoji, descrição, intensidade, contexto, fotos
6. Campos específicos por tipo (ex: price/rating para consumption)
7. Submit → adiciona ao dia atual (`logs[today].fragments`)
8. Fragmento aparece na feed

### 4. Fluxo de Destaques Canónicos
- Utilizador marca fragmento como `isHighlight = true`
- Aparece com badge ⭐ em todas as vistas
- Secção especial "Destaques Canónicos" em `/fragments`
- Filtragem visual e destaque na UI

---

## Funcionalidades-Chave

### 1. Swipe Deck (Cards Cronológicos)
**Componente:** `client/src/components/swipe-deck/SwipeDeck.tsx`

- Interface de swipe estilo "stories"
- Sequência de 9 mandatory cards + dynamic optional cards
- Tracking de progresso
- Permite voltar atrás
- Guarda estado parcial
- Animações suaves (Framer Motion)

### 2. Postal View (Vista do Dia)
**Página:** `client/src/pages/PostalView.tsx`

**Secções:**
- Header: data, tags de contexto, avaliação final
- Flip animation: frente ↔ verso
- **Frente (Bento Grid)**:
  - Cards visuais compactos: Sleep, Habits, Meals
  - Gráfico resumo
  - Fragmentos destacados
- **Verso (Timeline Detalhado)**:
  - Timeline cronológica de todos os períodos
  - Cards opcionais expandidos
  - Galeria de fotos (até 9)
  - Todos os fragmentos do dia

### 3. Feed de Fragmentos
**Página:** `client/src/pages/Fragments.tsx`

**Features:**
- Listagem cronológica de todos os fragmentos
- Filtros por tipo (8 categorias)
- Secção de "Destaques Canónicos" no topo
- Cards com foto de capa (se disponível)
- Modal de detalhe ao clicar
- Badges de tipo, intensidade emocional
- Metadados: localização, pessoas, timestamp
- Campos específicos visíveis (price, rating, etc.)

### 4. Histórico de Dias
**Página:** `client/src/pages/History.tsx`

- Calendário de dias registados
- Indicadores visuais de completude
- Cores por rating do dia
- Navegação rápida para dias específicos
- Vista de lista com resumos

### 5. Dashboard (Home)
**Página:** `client/src/pages/Home.tsx`

**Widgets:**
- Card principal: Estado dos mandatory cards (X/9 completos)
- Barra de progresso visual
- Tags de contexto do dia
- Quick actions: criar fragmento, preencher cards, ver postal
- Fragmentos de hoje (listagem compacta)
- Sugestão de optional cards

### 6. Card Registry System
**Arquivo:** `client/src/lib/cardRegistry.ts`

Sistema centralizado que:
- Define todos os 16 cards (9 mandatory + 7 optional)
- Ordem cronológica
- Ícones e metadados
- Função de completude para cada card
- Lógica de sugestões automáticas
- Fácil adição de novos cards

---

## Componentes Principais

### Daily Cards (24 componentes)
**Localização:** `client/src/components/daily/`

**Mandatory Cards (9):**
- `SleepCard.tsx` - Card de sono
- `ContextCard.tsx` - Tags, locais, pessoas
- `MorningPeriodCard.tsx` - Período manhã
- `LunchMealCard.tsx` - Refeição almoço
- `HabitCard.tsx` - Hábitos com streaks
- `AfternoonPeriodCard.tsx` - Período tarde
- `DinnerMealCard.tsx` - Refeição jantar
- `NightPeriodCard.tsx` - Período noite + fotos
- `EvaluationCard.tsx` - Avaliação final

**Optional Cards (7):**
- `WeatherCard.tsx` - Condições meteorológicas
- `PcActivitiesCard.tsx` - Atividades PC
- `GymCard.tsx` - Treino físico
- `DetailedMediaCard.tsx` - Média consumida
- `FinancesCard.tsx` - Finanças
- `LearningsCard.tsx` - Aprendizagens
- `SpecialMealCard.tsx` - Refeição especial

**Outros Componentes Daily:**
- `BentoGrid.tsx` - Layout em grid para postal view
- `DailyTimeline.tsx` - Timeline vertical do dia
- `FragmentCard.tsx` - Card de fragmento individual
- `PhotoGallery.tsx` - Galeria de até 9 fotos
- `DatePickerDrawer.tsx` - Seletor de data
- `EditCompleteLogDialog.tsx` - Modal de edição completa
- `OptionalCardSelector.tsx` - Seleção de optional cards

### Fragments
**Localização:** `client/src/components/fragments/`

- `CategorySelector.tsx` - Drawer de seleção de tipo de fragmento
- `TypedFragmentForm.tsx` - Formulário dinâmico por tipo (usa fragmentTypeConfig)

### Swipe Deck
**Localização:** `client/src/components/swipe-deck/`

- `SwipeDeck.tsx` - Container do swipe deck
- `SphereCard.tsx` - Card individual (usado para cada card cronológico)

### UI Primitives
**Localização:** `client/src/components/ui/`

Componentes baseados em shadcn/ui (Radix UI + Tailwind):
- 60+ componentes de UI reutilizáveis
- `HighlightBadge.tsx` - Badge customizado para destaques

### Layout
**Localização:** `client/src/components/layout/`

- `MobileShell.tsx` - Container principal com navegação bottom tab

---

## Conceitos-Chave de UX

### 1. Filosofia de Registo
- **Cronológico**: Fluxo linear que acompanha o dia
- **Modular**: Cards independentes, fácil de preencher parcialmente
- **Visual + Quantitativo**: Fotos + scores numéricos + texto reflexivo
- **Flexível**: Mandatory cards garantem estrutura, optional cards permitem personalização

### 2. Gamificação Suave
- Progresso visual (X/9 mandatory cards)
- Streaks de hábitos automáticos
- Badges de destaque (⭐ canónico)
- Selo "Perfect Day" (rating = 9)
- Sentiment tags

### 3. Design Mobile-First
- Interface tipo "stories" (swipe deck)
- FAB para ações rápidas
- Drawers/sheets para formulários
- Bottom navigation
- Otimização para uso com uma mão
- Animações suaves

### 4. Valorização do Presente
- Foco no "hoje" (home page)
- Criação rápida de fragmentos (3 taps)
- Reflexão estruturada mas não pesada
- Registo visual imediato

### 5. Mandatory vs Optional Cards
- **Mandatory**: Estrutura fixa que garante consistência temporal
- **Optional**: Personalização conforme atividades do dia
- **Card Registry**: Gere sugestões inteligentes

---

## Personalização e Configurações

**Settings (`/settings`):**
- Wake goal (hora de acordar ideal)
- Hábitos personalizados (label + emoji + cor)
- Tema (dark/light)
- Notificações (planeado)

---

## Estado Atual do Projeto

### ✅ Implementado
- **Card-Based Daily Logging** (9 mandatory + 7 optional)
- **Card Registry System** (configuração centralizada)
- **Period-based logging** (morning/afternoon/night)
- **Structured meals** (lunch/dinner como objetos)
- **Day evaluation system** (rating + perfect day seal + sentiment tags)
- **Habits with streaks** (cálculo automático)
- **Sistema de Fragmentos** (8 tipos com configs específicas)
- **Destaques Canónicos** (isHighlight badge)
- **Persistência local** (Zustand + localStorage)
- **UI components completa** (shadcn/ui - 60+ componentes)
- **Todas as páginas funcionais** (Home, Fragments, History, PostalView, SwipeView, Settings, Onboarding)
- **Swipe Deck** com cards cronológicos
- **Postal View** com flip animation
- **Fragment Feed** com filtros
- **History** com calendário
- **Photo Gallery** (até 9 fotos por dia)
- **Migração de dados legacy** (compatibilidade com versões antigas)

### 📋 Planeado
- **Backend integration** (API + PostgreSQL)
  - Sincronização cliente-servidor
  - Database schema atualizado
- **Autenticação completa** (login/register/sessions)
- **Página de Insights avançada**
  - Gráficos de tendências
  - Análise de padrões
  - Visualizações de streaks
  - Estatísticas mensais/anuais
- **Upload de fotos real** (storage servidor)
- **Notas de voz** (recording + storage)
- **Export de dados** (PDF, JSON)
- **PWA offline-first** (service workers)
- **Notificações push** (lembretes de preenchimento)
- **Partilha de fragmentos** (social features)
- **Integração com wearables** (sleep tracking automático)

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

### Database (Futuro)
```bash
npm run db:push      # Push schema para PostgreSQL (quando integrado)
```

### Type Checking
```bash
npm run check        # TypeScript check
```

---

## Convenções de Código

### Nomenclatura
- **Componentes**: PascalCase (ex: `SleepCard.tsx`)
- **Hooks**: camelCase prefixado com `use` (ex: `useStore.ts`)
- **Utils/Libs**: camelCase (ex: `cardRegistry.ts`)
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
- Animações subtis

### 2. Visual Storytelling
- Uso abundante de emojis (identidade, rapidez)
- Fotografias como elemento central
- Cards tipo "postal" (memória tangível)
- Timeline visual do dia

### 3. Acessibilidade
- Contraste adequado (WCAG AA)
- Textos alternativos em imagens
- Navegação por teclado
- Estados de focus visíveis
- Dark mode

### 4. Performance
- Lazy loading de componentes
- Imagens otimizadas
- Bundle splitting
- LocalStorage-first (rápido, sem latência)

---

## Notas de Migração

### Campos Legacy (Mantidos para Compatibilidade)

O código mantém os seguintes campos por razões de compatibilidade, mas **não devem ser usados em novo código**:

- `dayType` → Usar `dayContext.tags`
- `spheres` → Sistema antigo de 8 esferas (removido)
- `spheresCompletion` → Tracking do sistema antigo (removido)
- `radar` → Sistema ainda mais antigo de 5 dimensões (removido)
- `finalScore` → Usar `dayEvaluation.overallRating`
- `habitsCompleted` → Usar `habits.completed`

### Funções de Migração

**Localização:** `client/src/lib/store.ts`

- `migrateLegacyLog(log)` - Converte estruturas antigas para novas
- `normalizeLog(log)` - Normaliza dados após carregamento
- Automático ao carregar logs do localStorage

### Como Adicionar um Novo Card

1. Criar componente em `client/src/components/daily/NewCard.tsx`
2. Adicionar tipo ao `DailyLog` em `store.ts`
3. Registar em `cardRegistry.ts`:
   ```typescript
   {
     id: 'newCard',
     title: 'New Card',
     icon: IconName,
     type: 'optional', // ou 'mandatory'
     category: 'activity',
     description: '...',
     checkCompletion: (log) => !!log.newCard && log.newCard.field !== ''
   }
   ```
4. Adicionar ao Swipe Deck sequence (se mandatory)
5. Adicionar ao Optional Card Selector (se optional)

---

## Glossário

- **Mandatory Card**: Card obrigatório na sequência cronológica do dia
- **Optional Card**: Card adicionado dinamicamente conforme atividades
- **Card Registry**: Sistema centralizado de configuração de cards
- **Fragmento**: Momento específico da vida registado (micro vs. dia = macro)
- **Destaque Canónico**: Fragmento marcado como momento-chave que define a vida
- **Postal View**: Vista completa e detalhada de um dia específico (frente/verso)
- **Swipe Deck**: Interface de swipe para preenchimento dos cards
- **Day Evaluation**: Avaliação final do dia (rating 1-9 + perfect day seal)
- **Streak**: Sequência de dias consecutivos com hábito completado
- **Period**: Período do dia (morning/afternoon/night) com events + reflections

---

## Recursos Úteis

### Design System
- **shadcn/ui**: https://ui.shadcn.com/
- **Radix UI**: https://www.radix-ui.com/
- **Tailwind CSS**: https://tailwindcss.com/

### Bibliotecas
- **Zustand**: https://zustand-demo.pmnd.rs/
- **React Hook Form**: https://react-hook-form.com/
- **Zod**: https://zod.dev/
- **Recharts**: https://recharts.org/
- **date-fns**: https://date-fns.org/
- **Framer Motion**: https://www.framer.com/motion/

---

## Contribuição

### Prioridades Atuais
1. **Backend Integration** - Conectar API + PostgreSQL
2. **Database Schema Update** - Atualizar para refletir nova estrutura
3. **Autenticação** - Implementar login/register completo
4. **Insights Page** - Gráficos e estatísticas avançadas
5. **Real Photo Upload** - Storage no servidor
6. **Voice Notes** - Recording + storage
7. **Data Export** - PDF e JSON
8. **Tests** - Unitários e E2E

### Áreas de Melhoria
- Virtualização de listas longas (fragments feed)
- Acessibilidade (ARIA, screen readers)
- PWA offline-first completo
- Internacionalização (i18n)
- Performance otimizations

---

## Contacto e Suporte

Este projeto é desenvolvido como uma aplicação pessoal de auto-conhecimento. Para questões técnicas ou sugestões, consulte o repositório do código.

---

**Última atualização**: 2026-01-02
**Versão**: 2.0.0 (Major architecture change: Card-Based System)
