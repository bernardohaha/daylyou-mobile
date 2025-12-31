📄 TECHNICAL_BRIEF.md

Daylyou — Technical Brief v0.1 (MVP Ritual)

1. Objetivo deste documento

Este documento define decisões técnicas mínimas e conscientes para permitir vibecoding eficaz no Daylyou.

Não pretende:

fechar arquitetura definitiva

antecipar escalabilidade

otimizar performance

Pretende:

evitar decisões contraditórias

manter coerência com o PRD de Conceito e UX

permitir iteração rápida com AI

2. Plataforma & Stack (decisão inicial)
Target

iOS e Android

Mobile-first

Uso diário, pessoal, íntimo

Stack recomendada (v0.1)

React Native + Expo

TypeScript

Expo Router (navegação simples)

State local simples (Context ou store leve)

Persistência local (AsyncStorage ou equivalente)

⚠️ Nada de backend nesta fase.
⚠️ Nada de autenticação.
⚠️ Nada de cloud sync.

3. Arquitetura de Ecrãs (v0.1)
Estrutura base
App
 └── Timeline (Folhas)
      ├── Daily Card (Frente)
      ├── Daily Card (Verso)
      └── Modal: Criar Fragmento

Navegação

Swipe horizontal → navegar dias (ontem ← hoje → amanhã)

Tap → virar folha (frente ↔ verso)

Long press → menu contextual do dia

Sem tabs complexos.
Sem sidebars.
Sem feed infinito.

4. Modelos de Dados (v0 – canónicos)
DailyCard
DailyCard {
  id: string
  date: string (YYYY-MM-DD)
  mood: number (1–9)
  tags: string[]
  photos: string[]
  highlightFragmentId?: string
}

Fragment
Fragment {
  id: string
  dayId: string
  title: string
  type: 'social' | 'media' | 'desporto' | 'emocional' | 'trabalho' | 'outro'
  emoji: string
  isHighlight: boolean
}


⚠️ Sem texto longo obrigatório
⚠️ Sem campos “analytics-heavy” nesta fase

5. Persistência (v0)

Local-first

Persistência simples (key-value)

Estrutura por dia

Exemplo conceptual:

storage/
 ├── days/
 │    ├── 2025-01-12.json
 │    ├── 2025-01-13.json
 └── fragments/
      ├── fragment_123.json


Objetivo:

Nunca perder dados do utilizador, mesmo offline.

6. UI & Gestos (não negociável)

Swipe horizontal = tempo

Tap = virar folha

Long press = edição

Feedback háptico leve ao virar

A UI nunca deve parecer:

dashboard

tracker de hábitos

app de produtividade

7. Fora de Escopo (MVP)

Autenticação

Cloud sync

Social / partilha

Rankings

Gamificação agressiva

Notificações push

Estatísticas globais

8. Critério de sucesso do MVP técnico

O MVP está “tecnicamente suficiente” quando:

Consigo criar um dia

Criar um fragmento

Navegar dias

Voltar a abrir a app e ver tudo igual

Sentir que estou a manusear algo meu