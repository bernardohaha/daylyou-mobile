📘 PRD DAYLYOU
Módulo: Daily Cards & Daylyou Fragmentos

Versão: v1.0 

1. VISÃO DO PRODUTO

O Daylyou é uma aplicação de registo consciente da vida quotidiana.

O seu propósito é ajudar o utilizador a:

sair do modo automático

ganhar consciência do tempo vivido

construir memória pessoal com significado

rever a sua vida como narrativa, não como estatística

Este PRD define os dois objetos nucleares do sistema:

Daily Card → a visão macro, simbólica e analítica de um dia

Daylyou Fragmentos → os episódios micro que dão alma e identidade à memória

O Daylyou não mede performance.
O Daylyou preserva presença.

2. PROBLEMA A RESOLVER
Problema principal

As pessoas vivem os dias em piloto automático e, ao fim do tempo:

lembram-se de poucos momentos concretos

não têm memória visual ou narrativa do quotidiano

reduzem a vida a rótulos vagos (“bom dia”, “dia mau”)

Problemas secundários

journaling clássico é pesado e pouco sustentável

trackers transformam a vida num dashboard mecânico

notas soltas não criam identidade nem memória durável

3. OBJETIVO DO MÓDULO

Criar um sistema que permita ao utilizador:

Registar o dia de forma estruturada, sem fricção

Capturar momentos significativos enquanto acontecem

Ser convidado (não forçado) a viver pelo menos 1 momento consciente por dia

Construir uma linha de memória visual, emocional e revisível ao longo do tempo

4. OBJETOS-CHAVE DO SISTEMA
🪪 4.1 DAILY CARD (1 por dia)
Definição

O Daily Card torna-se:

a célula-base do meu ano

o átomo simbólico da minha identidade

a peça de arquivo que diz: “Foi assim que vivi este dia.”

É a mistura de:

O que fiz

Como me senti

Quem vi

O que consumi

Onde estive

Qual foi a energia do dia

Pequenos highlights visuais e emocionais

E tudo isto comprimido num card belíssimo, com hierarquia de importância, ícones simbólicos, mini métricas e composição gráfica única.


4.1.A — Frente Emocional (Timeline)
Conteúdo obrigatório

Humor geral do dia

emoji ou escala curta (1–9)

Qualidade percebida do dia (1 tag)

core

meh

relevante

um dia fixe

Conteúdo recomendado

Intenção ↔ Resultado

1 frase curta (máx. 1 linha)

Conteúdo opcional

Destaque do Dia

ligação visual a 1 Daylyou Fragmento

funciona como âncora de memória

4.1.B — Verso Analítico .

O preenchimento do Daily Card é feito através de um
Swipe Deck Interativo.

Cada categoria aparece como um cartão individual, onde o utilizador:

faz swipe

ajusta sliders

toca em opções rápidas

Nunca uma lista longa de perguntas.
Depois ao clicar no card virava e mostrava os dados mais analiticos e especificos: Mini timeline do dia (manhã–tarde–noite) Gráfico micro (sparkline do humor ou produtividade) Heatmap interno dos hábitos Destaque às interações: “Tive com Ana, João, Pai” Preview das médias consumidas (icones tiny) Locais onde estive balanço financeiro do dia Frase do dia (aprendizagem ou insight pessoal) Micro-área de journaling

Estrutura do Swipe Deck (8 Esferas)

Estado Interno

Intenção & Direção

Tempo & Ritmo

Contexto & Ambiente

Vida Social

Ações & Comportamentos

Conteúdo & Estímulos

Significado & Marcas

Cada esfera:

é preenchida maioritariamente por cliques

demora < 30 segundos

Visualização de Dados

As 8 Esferas geram um Spider Chart (Radar Chart).

aparece na frente do Daily Card (versão compacta)

o polígono muda conforme o tipo de dia vivido

cada dia tem uma assinatura visual única

🌅 5. RITUAL DA MANHÃ (Morning Trigger)
Objetivo

Criar um gatilho natural de entrada no dia.

Morning Card

Ao abrir a app pela primeira vez num novo dia:

O utilizador é recebido por um Morning Card, onde regista:

hora de adormecer

hora de acordar

qualidade do sono

objetivo pessoal (ex: “acordar antes das 10h”)

Este momento:

cria automaticamente o Daily Card vazio

ancora o início do dia no sistema

não é obrigatório nem punitivo

🧩 4.2 DAYLYOU FRAGMENTOS (0–∞ por dia)
Definição

Os Daylyou Fragmentos são episódios específicos vividos ao longo do dia que merecem ser lembrados.

Não são:

hábitos

estatísticas

notas genéricas

São:

acontecimentos reais

localizados no tempo

emocionalmente relevantes

Estrutura de um Daylyou Fragmento
1. Título curto

Manual ou sugerido automaticamente.

Ex:

“Jantar inesperado depois do cinema”

“Sporting no estádio com chuva”

2. Tipo de Fragmento (1 escolha)

🎭 Social

🎬 Cultural

⚽ Desporto

🧠 Intelectual

💼 Trabalho

🛍️ Consumo

❤️ Emocional

✨ Aleatório

3. Contexto rápido

📍 Local

👥 Pessoas (tags)

🕒 Momento do dia (manhã / tarde / noite)

4. Emoção do momento

emoji obrigatório

intensidade opcional (1–9)

5. Conteúdo associado (opcional, mas estruturado)

Se aplicável, o Fragmento liga-se a objetos ricos do Daylyou:

Filme / Série / Livro / Música / Podcast

Jogo / Clube / Evento desportivo

Produto comprado

⚠️ Estes conteúdos não são texto solto — são entidades reutilizáveis.

6. Marca visual (âncora de memória)

Pelo menos uma é fortemente recomendada:

📷 fotografia

🎙️ nota de voz

📝 frase curta

7. Nota livre

até 3 linhas

sem obrigação narrativa

8. Daylyou Badge (Destaque)

Toggle opcional para marcar o Fragmento como canónico.

No código:

is_highlight: boolean

6. RELAÇÃO ENTRE DAILY CARD & FRAGMENTOS
Regras estruturais

Um Daily Card pode existir sem Fragmentos

Um Fragmento não pode existir sem um Daily Card

Todo Fragmento está associado a um dia específico

Destaque do Dia (mecânica central)

O sistema convida o utilizador a escolher 1 Fragmento como Destaque do Dia.

Esse destaque:

aparece na frente do Daily Card

funciona como âncora principal de memória

Objetivo psicológico:

“Mesmo um dia banal teve pelo menos um momento que valeu a pena.”

⚠️ Nunca é obrigatório
⚠️ Nunca é moralista

7. EXPERIÊNCIA DO UTILIZADOR (UX)
Fluxo natural

Ao longo do dia
→ criar Fragmentos rápidos (≤10s)

À noite ou no dia seguinte
→ preencher o Daily Card via Swipe Deck
→ escolher (ou não) um Destaque

Princípios UX (não negociáveis)

logging rápido

foco visual

zero culpa

zero comparação

sensação de coleção pessoal

8. TIMELINES & VISTAS
Vista Principal

Timeline de Daily Cards

mostra apenas a frente emocional

Vista de Fragmentos

Filtrável por:

dia

tipo

pessoas

emoção

Vista Memória (futura)

“Momentos que te marcaram”

“Fragmentos com X pessoa”

“Dias com Destaque”

9. REPRESENTAÇÃO CONCEPTUAL DO TEMPO 

No Daylyou, o tempo não é representado como uma linha abstrata nem como estatística acumulada.

É representado como um arquivo pessoal simbólico.

Metáfora estrutural

Cada dia é representado como uma folha individual

Cada mês é um capítulo que agrupa essas folhas

Cada ano é um dossiê que reúne todos os capítulos

Esta metáfora orienta:

a forma como os dias são visualizados

a navegação temporal

a experiência de revisão mensal e anual

Significado conceptual

A escolha de uma metáfora física e arquivística reforça a ideia de que:

o tempo vivido tem peso

a memória merece durabilidade

cada dia pode ser revisto como um documento com valor

Os detalhes visuais, materiais e de interação desta metáfora são definidos no PRD de Design/UX, mantendo o PRD de Conceito focado na estrutura e filosofia do sistema.

10. PRINCÍPIOS FILOSÓFICOS (CORE)

O sistema não julga

O sistema não compara

O sistema não otimiza performance

O sistema valoriza presença

Um dia vale a pena
mesmo que só por um momento.

11. MÉTRICAS DE SUCESSO (QUALITATIVAS)

Utilizador regista dias consecutivos

Utilizador cria Fragmentos espontaneamente

Utilizador escolhe Destaques

Utilizador revisita dias passados

Utilizador refere “lembrar-se melhor da sua vida”

12. FORA DE ESCOPO (MVP)

feed social

partilha pública

gamificação agressiva

rankings

streaks obrigatórios

13. RESUMO FINAL

O Daylyou não pergunta:

“Foste produtivo?”

Pergunta:

“Viveste?”

Os Daily Cards dão estrutura ao tempo.
Os Daylyou Fragmentos dão alma à memória.

Isto não é apenas um produto.
É uma posição ética sobre como viver.