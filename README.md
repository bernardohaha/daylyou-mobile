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

## 🎯 Dois Pilares Fundamentais

### 1. Card-Based Daily Logging (Registo Diário Cronológico)

Sistema de **Daily Cards** estruturado cronologicamente que acompanha o fluxo natural do seu dia.

**Sistema de Frente/Verso:**
- **Frente**: Resumo visual do dia (interface compacta e gráfica)
- **Verso**: Timeline detalhado e estatístico (dados completos)

#### 9 Cards Obrigatórios (Fluxo Cronológico)

Sequência fixa que estrutura o seu dia:

1. 🌙 **Sleep** - Como dormiu (horas, qualidade, acordou cedo?)
2. 📍 **Context** - Contexto do dia (work/off/vacation, locais, pessoas)
3. 🌅 **Morning** - O que aconteceu de manhã + reflexões
4. 🍽️ **Lunch** - O que comeu ao almoço + com quem
5. ✓ **Habits** - Hábitos completados (com tracking de streaks automático)
6. 🌞 **Afternoon** - O que aconteceu à tarde + reflexões
7. 🍽️ **Dinner** - O que comeu ao jantar + com quem
8. 🌃 **Night** - Resumo e reflexão final + fotos do dia
9. ⭐ **Evaluation** - Como avalia o dia (1-9) + selo "Perfect Day" + destaque

#### 7 Cards Opcionais (Adicione Conforme Necessário)

Personalize o seu dia com cards adicionais:

1. 🌤️ **Weather** - Condições meteorológicas do dia
2. 💻 **PC Activities** - Horas e atividades no computador (trabalho, gaming, etc.)
3. 💪 **Gym** - Treino físico (tipo, grupos musculares, exercícios)
4. 🎬 **Detailed Media** - Filmes, séries, livros consumidos (com ratings e favoritos)
5. 💰 **Finances** - Transações financeiras (despesas/receitas categorizadas)
6. 📚 **Learnings** - Aprendizagens do dia (com fonte e emoji)
7. 🍴 **Special Meal** - Refeição especial em restaurante

**Card Registry System**: Sistema inteligente que sugere cards opcionais conforme suas atividades (ex: sugere Gym card quando marca hábito "Exercício").

### 2. Daylyou Fragmentos (Momentos Micro)

Registos de **momentos específicos** da vida (granularidade micro vs. dia inteiro macro).

**8 Tipos de Fragmentos:**
- 🎭 **Social** - Eventos sociais, encontros
- 🎬 **Cultural** - Filmes, Séries, Livros, Podcasts, Músicas
- ⚽ **Desporto** - Atividades desportivas assistidas ou praticadas
- 🧠 **Intelectual** - Aprendizagens, frases marcantes
- 💼 **Trabalho** - Momentos profissionais significativos
- 🛍️ **Consumo** - Compras, produtos (com preço e rating)
- ❤️ **Emocional** - Momentos marcantes emocionalmente
- ✨ **Aleatório** - Outros momentos

**Componentes de um Fragmento:**
- Título e emoji obrigatórios
- Descrição e intensidade emocional (1-9)
- Contexto: localização, pessoas envolvidas, período do dia
- Marcas visuais: fotos, notas de voz, frase curta
- Badge **"Destaque Canónico" ⭐** - momentos que definem a sua vida

---

## 🛠️ Stack Tecnológico

### Frontend
- **Framework**: React 19.2.0 + TypeScript 5.6.3
- **Build Tool**: Vite 7.1.9
- **Routing**: Wouter 3.3.5 (lightweight routing)
- **State Management**: Zustand 5.0.9 (com persistência local)
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

**Nota Importante**: Atualmente a aplicação funciona totalmente em modo **local** (localStorage). A integração com backend PostgreSQL está planeada mas não implementada.

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
│   │       │   ├── daily/          # 24 Daily Cards (9 mandatory + 7 optional)
│   │       │   ├── fragments/      # Componentes de Fragmentos
│   │       │   ├── layout/         # Layout components
│   │       │   ├── swipe-deck/     # Swipe Deck interface
│   │       │   └── ui/             # 60+ UI primitives (shadcn/ui)
│   │       ├── hooks/              # Custom React hooks
│   │       ├── lib/                # Utilities e state
│   │       │   ├── cardRegistry.ts      # Card configuration ⭐
│   │       │   ├── fragmentTypeConfig.ts # Fragment configs ⭐
│   │       │   └── store.ts             # Zustand store ⭐
│   │       ├── pages/              # Page components
│   │       │   ├── Home.tsx        # Dashboard principal
│   │       │   ├── Fragments.tsx   # Feed de fragmentos
│   │       │   ├── History.tsx     # Calendário de dias
│   │       │   ├── PostalView.tsx  # Vista detalhada do dia
│   │       │   ├── SwipeView.tsx   # Preenchimento de cards
│   │       │   ├── Insights.tsx    # Estatísticas (placeholder)
│   │       │   ├── Settings.tsx    # Configurações
│   │       │   └── Onboarding.tsx  # Setup inicial
│   │       ├── App.tsx             # Root component + Router
│   │       └── main.tsx            # Entry point
│   ├── server/                     # Backend (não integrado)
│   ├── shared/                     # Shared code
│   ├── package.json
│   ├── tsconfig.json
│   └── vite.config.ts
├── CLAUDE.md                       # Documentação técnica detalhada
└── README.md                       # Este arquivo
```

---

## 🚀 Como Começar

### Pré-requisitos
- Node.js (versão 18 ou superior)
- npm

### Instalação

```bash
# Clone o repositório
git clone <repository-url>
cd daylyou-mobile/Daily-Journal-Mobile

# Instale as dependências
npm install
```

### Desenvolvimento

```bash
# Inicia servidor de desenvolvimento (frontend + backend)
npm run dev

# Apenas frontend (porta 5000)
npm run dev:client
```

**Nota**: A aplicação funciona totalmente em modo local com localStorage. Não é necessário configurar base de dados para desenvolvimento.

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
/insights            → Insights (estatísticas - em desenvolvimento)
/settings            → Settings (configurações)
/day/:date           → PostalView (vista detalhada do dia - frente/verso)
/fill/:date          → SwipeView (preencher cards cronológicos)
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
- **Tap** → Virar folha (frente ↔ verso) no PostalView
- **Long press** → Menu de Edição

### Daily Card vs Fragmento

- **Daily Card**: Visão macro do dia inteiro (estrutura cronológica)
- **Fragmento**: Episódios micro que dão alma e identidade à memória

Um Daily Log pode existir sem Fragmentos, mas um Fragmento sempre pertence a um dia específico.

### Mandatory vs Optional Cards

- **Mandatory Cards** (9): Sequência cronológica fixa que estrutura o dia
  - Garantem consistência temporal
  - Sleep → Context → Morning → Lunch → Habits → Afternoon → Dinner → Night → Evaluation

- **Optional Cards** (7): Adicionados dinamicamente conforme atividades do dia
  - Personalizam o registo
  - Sugeridos automaticamente pelo Card Registry System

- **Card Registry**: Sistema inteligente que gere completude e sugestões
  - Exemplo: Sugere Gym card quando hábito "Exercício" é marcado

---

## 📊 Estado Atual do Projeto

### ✅ Implementado (Funcional)

**Core Features**:
- Card-Based Daily Logging (9 mandatory + 7 optional cards)
- Card Registry System (configuração centralizada e sugestões)
- Period-based logging (morning/afternoon/night com eventos + reflexões)
- Structured meals (lunch/dinner como objetos estruturados)
- Day evaluation system (rating 1-9 + Perfect Day seal + sentiment tags)
- Habits with automatic streaks
- Sistema de Fragmentos (8 tipos com configurações específicas)
- Destaques Canónicos (highlight badge)
- Persistência local completa (Zustand + localStorage)

**Pages**:
- Home dashboard (progresso do dia, quick actions, fragmentos)
- Fragments feed (filtros por tipo, destaques canónicos)
- History (calendário visual de dias)
- PostalView (vista detalhada com flip frente/verso)
- SwipeView (preenchimento de cards cronológicos)
- Settings (configuração de hábitos, tema)
- Onboarding (setup inicial)

**UI/UX**:
- UI components completa (60+ componentes shadcn/ui)
- Swipe Deck interface (estilo "stories")
- Bento Grid layout para postal view
- Daily Timeline vertical
- Photo Gallery (até 9 fotos por dia)
- Animações suaves (Framer Motion)
- Dark mode
- Mobile-first responsive design

### 📋 Planeado (Próximas Features)

**Backend & Sync**:
- Integração com backend PostgreSQL
- Sincronização cliente-servidor
- Autenticação completa (login/register/sessions)
- Database schema atualizado

**Advanced Features**:
- Página de Insights avançada (gráficos, tendências, padrões)
- Upload de fotos real (storage no servidor)
- Notas de voz (recording + storage)
- Export de dados (PDF, JSON)
- PWA offline-first completo (service workers)
- Notificações push (lembretes de preenchimento)
- Partilha de fragmentos (social features)
- Integração com wearables (sleep tracking automático)

---

## 🧩 Componentes Principais

### Daily Cards (24 componentes)
**Localização**: `client/src/components/daily/`

**9 Mandatory Cards**:
- Sleep, Context, Morning, Lunch, Habits, Afternoon, Dinner, Night, Evaluation

**7 Optional Cards**:
- Weather, PC Activities, Gym, Detailed Media, Finances, Learnings, Special Meal

**Outros**:
- BentoGrid, DailyTimeline, PhotoGallery, FragmentCard, OptionalCardSelector

### Fragments
**Localização**: `client/src/components/fragments/`

- CategorySelector (drawer de seleção de tipo)
- TypedFragmentForm (formulário dinâmico por tipo)

### Swipe Deck
**Localização**: `client/src/components/swipe-deck/`

- SwipeDeck (container)
- SphereCard (card individual, usado para cada card cronológico)

### UI Primitives
**Localização**: `client/src/components/ui/`

- 60+ componentes baseados em shadcn/ui (Radix UI + Tailwind)
- Accordion, Alert, Avatar, Badge, Button, Calendar, Card, Checkbox, Dialog, Drawer, Input, Select, Slider, Toast, etc.

---

## 🔧 Convenções de Código

### Nomenclatura
- **Componentes**: PascalCase (ex: `SleepCard.tsx`)
- **Hooks**: camelCase prefixado com `use` (ex: `useStore.ts`)
- **Utils/Libs**: camelCase (ex: `cardRegistry.ts`)
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

## 🎨 Princípios de Design

### Minimalismo Contemplativo
- Espaço em branco generoso
- Tipografia clara e hierarquizada
- Cores suaves com acentos intencionais
- Animações subtis e intencionais

### Visual Storytelling
- Uso abundante de emojis (identidade, rapidez)
- Fotografias como elemento central
- Cards tipo "postal" (memória tangível)
- Timeline visual do dia

### Mobile-First
- Interface tipo "stories" (swipe deck)
- FAB para ações rápidas
- Drawers/sheets para formulários
- Bottom navigation
- Otimização para uso com uma mão

### Performance & Acessibilidade
- Lazy loading de componentes
- Bundle splitting
- LocalStorage-first (rápido, sem latência)
- Dark mode
- Contraste WCAG AA

---

## 🤝 Contribuição

### Prioridades Atuais
1. **Backend Integration** - Conectar API + PostgreSQL + sincronização
2. **Autenticação** - Sistema completo de login/register
3. **Insights Page** - Gráficos, tendências, análise de padrões
4. **Photo Upload** - Storage real no servidor
5. **Voice Notes** - Recording + playback + storage
6. **Data Export** - PDF e JSON
7. **PWA Offline-First** - Service workers
8. **Tests** - Unitários e E2E

### Áreas de Melhoria
- Performance de listas longas (virtualização)
- Acessibilidade (ARIA, screen readers)
- Internacionalização (i18n)
- Analytics e métricas
- Onboarding melhorado

---

## 📚 Documentação Adicional

Para documentação técnica completa, consulte:

- **CLAUDE.md** - Documentação técnica detalhada (arquitetura, data model, componentes, fluxos)
- **Code Comments** - Comentários inline no código para lógica complexa

---

## 🌟 Características Únicas

### Card Registry System
Sistema centralizado que:
- Define configuração de todos os cards
- Gere ordem cronológica
- Calcula completude automaticamente
- Sugere optional cards inteligentemente
- Permite fácil adição de novos cards

### Period-Based Logging
Estrutura temporal natural:
- Morning: eventos + reflexões
- Afternoon: eventos + reflexões
- Night: resumo + reflexão final + fotos

### Habits with Automatic Streaks
- Tracking automático de sequências
- Visualização de progresso
- Gamificação suave sem pressão

### Fragment Type Configurations
- Configurações específicas por tipo de fragmento
- Campos required/recommended/hidden por tipo
- Prompts e ordenação personalizados
- Special fields (mediaSelector, sportType, price, rating)

---

## 💡 Filosofia de Uso

O Daylyou foi desenhado para ser:

- **Não-invasivo**: Preencha quando quiser, como quiser
- **Estruturado mas flexível**: Mandatory cards dão estrutura, optional cards dão liberdade
- **Visual e reflexivo**: Fotos + texto + números = memória rica
- **Cronológico**: Acompanha o fluxo natural do seu dia
- **Significativo**: Foca em momentos que importam (fragmentos + destaques)

### Zero Culpa, Zero Comparação

- Não há "dias perfeitos" obrigatórios (só um selo quando VOCÊ decide rating = 9)
- Não há streaks obrigatórios (são informativos, não coercivos)
- Não há comparação com outros utilizadores
- Não há notificações intrusivas (planeadas como opcionais)

---

## 📄 Licença

MIT License

---

## 🙏 Agradecimentos

Este projeto é desenvolvido como uma aplicação pessoal de auto-conhecimento. Inspirado na necessidade de criar memória pessoal significativa e valorizar o presente.

---

**Última atualização**: 2026-01-02
**Versão**: 2.0.0 (Major architecture change: Card-Based System)
