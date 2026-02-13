<html lang="pt-BR" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Linha do Tempo - Engenharia de Software</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&amp;family=JetBrains+Mono:wght@400;500&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    
    * {
      font-family: 'Space Grotesk', sans-serif;
    }
    
    .mono {
      font-family: 'JetBrains Mono', monospace;
    }
    
    .timeline-line {
      background: linear-gradient(180deg, 
        var(--primary-action) 0%, 
        var(--secondary-action) 50%, 
        var(--primary-action) 100%);
    }
    
    .card-expanded {
      max-height: 500px;
    }
    
    .card-collapsed {
      max-height: 0;
    }
    
    .phase-card {
      transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }
    
    .phase-card:hover {
      transform: translateY(-4px);
    }
    
    .lesson-card {
      transition: all 0.3s ease;
    }
    
    .lesson-card:hover {
      transform: translateX(8px);
    }
    
    .pulse-dot {
      animation: pulse 2s infinite;
    }
    
    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 1; }
      50% { transform: scale(1.2); opacity: 0.7; }
    }
    
    @keyframes slideIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .animate-slide {
      animation: slideIn 0.5s ease forwards;
    }
    
    .progress-fill {
      transition: width 0.8s ease;
    }
    
    :root {
      --background: #0f0f23;
      --surface: #1a1a2e;
      --text: #e4e4f0;
      --primary-action: #6366f1;
      --secondary-action: #22d3ee;
    }
    
    .scrollbar-hide::-webkit-scrollbar {
      display: none;
    }
    
    .scrollbar-hide {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full w-full m-0 p-0" style="background: var(--background);">
  <div id="app" class="h-full w-full overflow-auto scrollbar-hide"><!-- Header -->
   <header class="sticky top-0 z-50 px-6 py-4" style="background: linear-gradient(180deg, var(--background) 100%, transparent 0%);">
    <div class="max-w-5xl mx-auto">
     <div class="flex items-center justify-between">
      <div>
       <h1 id="course-title" class="text-2xl md:text-3xl font-bold" style="color: var(--text);">🚀 Jornada da Qualidade de Software</h1>
       <p id="course-subtitle" class="text-sm md:text-base mt-1 opacity-80" style="color: var(--secondary-action);">Do conceito à entrega</p>
      </div>
      <div class="hidden md:flex items-center gap-3 px-4 py-2 rounded-full" style="background: var(--surface);"><span class="text-sm" style="color: var(--text);">Progresso</span>
       <div class="w-32 h-2 rounded-full overflow-hidden" style="background: var(--background);">
        <div id="progress-bar" class="h-full rounded-full progress-fill" style="width: 0%; background: linear-gradient(90deg, var(--primary-action), var(--secondary-action));"></div>
       </div><span id="progress-text" class="text-sm mono" style="color: var(--secondary-action);">0%</span>
      </div>
     </div>
    </div>
   </header><!-- Main Content -->
   <main class="px-4 md:px-6 pb-12">
    <div class="max-w-5xl mx-auto relative"><!-- Timeline Line -->
     <div class="absolute left-6 md:left-1/2 top-0 bottom-0 w-1 timeline-line rounded-full transform md:-translate-x-1/2" style="opacity: 0.3;"></div><!-- Phases Container -->
     <div id="timeline-container" class="space-y-8 md:space-y-12"><!-- Phase 1: Montando a Caixa de Ferramentas -->
      <div class="phase-section animate-slide" style="animation-delay: 0.1s;">
       <div class="relative flex items-start md:items-center gap-4 md:gap-8"><!-- Timeline Node -->
        <div class="relative z-10 flex-shrink-0 w-12 h-12 rounded-full flex items-center justify-center shadow-lg pulse-dot" style="background: var(--primary-action);"><span class="text-2xl">🧰</span>
        </div><!-- Phase Card -->
        <div class="flex-1 phase-card rounded-2xl p-5 md:p-6 cursor-pointer" style="background: var(--surface); border: 1px solid rgba(99, 102, 241, 0.3);" onclick="togglePhase('phase1')">
         <div class="flex items-center justify-between">
          <div><span class="mono text-xs px-2 py-1 rounded-full" style="background: var(--primary-action); color: var(--text);">FASE 1</span>
           <h2 class="text-xl md:text-2xl font-bold mt-2" style="color: var(--text);">Montando a Caixa de Ferramentas</h2>
           <p class="text-sm mt-1 opacity-70" style="color: var(--text);">Fundamentos e padrões essenciais</p>
          </div>
          <div class="flex items-center gap-2"><span class="mono text-sm" style="color: var(--secondary-action);">3 aulas</span>
           <svg id="arrow-phase1" class="w-6 h-6 transition-transform duration-300" style="color: var(--secondary-action);" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
           </svg>
          </div>
         </div><!-- Expanded Content -->
         <div id="phase1-content" class="overflow-hidden transition-all duration-500 card-collapsed">
          <div class="mt-6 space-y-3">
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson1')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: var(--primary-action); color: var(--text);">
              01
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Princípios SOLID e GRASP</h3>
              <div id="lesson1-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 <strong>SOLID:</strong> Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion</p>
               <p class="mt-2">📌 <strong>GRASP:</strong> General Responsibility Assignment Software Patterns - padrões para atribuição de responsabilidades</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson2')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: var(--primary-action); color: var(--text);">
              02
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Arquitetura de Software</h3>
              <div id="lesson2-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Padrões arquiteturais: MVC, MVVM, Clean Architecture</p>
               <p class="mt-2">📌 Decisões de design que impactam todo o sistema</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson3')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: var(--primary-action); color: var(--text);">
              03
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Padrões de Projetos GoF</h3>
              <div id="lesson3-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 <strong>Criacionais:</strong> Factory, Singleton, Builder</p>
               <p class="mt-1">📌 <strong>Estruturais:</strong> Adapter, Decorator, Facade</p>
               <p class="mt-1">📌 <strong>Comportamentais:</strong> Observer, Strategy, Command</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
          </div>
         </div>
        </div>
       </div>
      </div><!-- Phase 2: Entendendo o Problema -->
      <div class="phase-section animate-slide" style="animation-delay: 0.2s;">
       <div class="relative flex items-start md:items-center gap-4 md:gap-8">
        <div class="relative z-10 flex-shrink-0 w-12 h-12 rounded-full flex items-center justify-center shadow-lg" style="background: #8b5cf6;"><span class="text-2xl">🔍</span>
        </div>
        <div class="flex-1 phase-card rounded-2xl p-5 md:p-6 cursor-pointer" style="background: var(--surface); border: 1px solid rgba(139, 92, 246, 0.3);" onclick="togglePhase('phase2')">
         <div class="flex items-center justify-between">
          <div><span class="mono text-xs px-2 py-1 rounded-full" style="background: #8b5cf6; color: var(--text);">FASE 2</span>
           <h2 class="text-xl md:text-2xl font-bold mt-2" style="color: var(--text);">Entendendo o Problema</h2>
           <p class="text-sm mt-1 opacity-70" style="color: var(--text);">Análise e modelagem de requisitos</p>
          </div>
          <div class="flex items-center gap-2"><span class="mono text-sm" style="color: var(--secondary-action);">4 aulas</span>
           <svg id="arrow-phase2" class="w-6 h-6 transition-transform duration-300" style="color: var(--secondary-action);" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
           </svg>
          </div>
         </div>
         <div id="phase2-content" class="overflow-hidden transition-all duration-500 card-collapsed">
          <div class="mt-6 space-y-3">
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson4')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #8b5cf6; color: var(--text);">
              04
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Análise de Domínio</h3>
              <div id="lesson4-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Identificação de entidades, regras de negócio e contextos delimitados</p>
               <p class="mt-2">📌 Domain-Driven Design (DDD) básico</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson5')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #8b5cf6; color: var(--text);">
              05
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Modelagem Conceitual</h3>
              <div id="lesson5-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Diagramas UML: Classes, Casos de Uso, Sequência</p>
               <p class="mt-2">📌 Representação visual do sistema</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson6')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #8b5cf6; color: var(--text);">
              06
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Histórias de Usuário e Objetivos SMART</h3>
              <div id="lesson6-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 "Como [usuário], quero [funcionalidade], para [benefício]"</p>
               <p class="mt-2">📌 SMART: Específico, Mensurável, Alcançável, Relevante, Temporal</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson7')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #8b5cf6; color: var(--text);">
              07
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Priorização de Requisitos</h3>
              <div id="lesson7-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 MoSCoW: Must, Should, Could, Won't</p>
               <p class="mt-2">📌 Matriz de valor vs esforço</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
          </div>
         </div>
        </div>
       </div>
      </div><!-- Phase 3: Criando uma Solução Válida -->
      <div class="phase-section animate-slide" style="animation-delay: 0.3s;">
       <div class="relative flex items-start md:items-center gap-4 md:gap-8">
        <div class="relative z-10 flex-shrink-0 w-12 h-12 rounded-full flex items-center justify-center shadow-lg" style="background: #10b981;"><span class="text-2xl">✅</span>
        </div>
        <div class="flex-1 phase-card rounded-2xl p-5 md:p-6 cursor-pointer" style="background: var(--surface); border: 1px solid rgba(16, 185, 129, 0.3);" onclick="togglePhase('phase3')">
         <div class="flex items-center justify-between">
          <div><span class="mono text-xs px-2 py-1 rounded-full" style="background: #10b981; color: var(--text);">FASE 3</span>
           <h2 class="text-xl md:text-2xl font-bold mt-2" style="color: var(--text);">Criando uma Solução Válida</h2>
           <p class="text-sm mt-1 opacity-70" style="color: var(--text);">Testes e validação de código</p>
          </div>
          <div class="flex items-center gap-2"><span class="mono text-sm" style="color: var(--secondary-action);">4 aulas</span>
           <svg id="arrow-phase3" class="w-6 h-6 transition-transform duration-300" style="color: var(--secondary-action);" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
           </svg>
          </div>
         </div>
         <div id="phase3-content" class="overflow-hidden transition-all duration-500 card-collapsed">
          <div class="mt-6 space-y-3">
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson8')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #10b981; color: var(--text);">
              08
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Desenvolvimento Orientado a Testes</h3>
              <div id="lesson8-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 TDD: Red → Green → Refactor</p>
               <p class="mt-2">📌 Escreva o teste antes do código!</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson9')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #10b981; color: var(--text);">
              09
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Plano de Testes I</h3>
              <div id="lesson9-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Testes unitários e de integração</p>
               <p class="mt-2">📌 Cobertura de código e métricas</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson10')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #10b981; color: var(--text);">
              10
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Plano de Testes II</h3>
              <div id="lesson10-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Testes de sistema e aceitação</p>
               <p class="mt-2">📌 Automação e CI/CD</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson11')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #10b981; color: var(--text);">
              11
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Plano de Testes III</h3>
              <div id="lesson11-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Testes de performance e segurança</p>
               <p class="mt-2">📌 Testes exploratórios</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
          </div>
         </div>
        </div>
       </div>
      </div><!-- Phase 4: Refinando a Solução -->
      <div class="phase-section animate-slide" style="animation-delay: 0.4s;">
       <div class="relative flex items-start md:items-center gap-4 md:gap-8">
        <div class="relative z-10 flex-shrink-0 w-12 h-12 rounded-full flex items-center justify-center shadow-lg" style="background: #f59e0b;"><span class="text-2xl">💎</span>
        </div>
        <div class="flex-1 phase-card rounded-2xl p-5 md:p-6 cursor-pointer" style="background: var(--surface); border: 1px solid rgba(245, 158, 11, 0.3);" onclick="togglePhase('phase4')">
         <div class="flex items-center justify-between">
          <div><span class="mono text-xs px-2 py-1 rounded-full" style="background: #f59e0b; color: #1a1a2e;">FASE 4</span>
           <h2 class="text-xl md:text-2xl font-bold mt-2" style="color: var(--text);">Refinando a Solução</h2>
           <p class="text-sm mt-1 opacity-70" style="color: var(--text);">Qualidade e entrega final</p>
          </div>
          <div class="flex items-center gap-2"><span class="mono text-sm" style="color: var(--secondary-action);">4 aulas</span>
           <svg id="arrow-phase4" class="w-6 h-6 transition-transform duration-300" style="color: var(--secondary-action);" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
           </svg>
          </div>
         </div>
         <div id="phase4-content" class="overflow-hidden transition-all duration-500 card-collapsed">
          <div class="mt-6 space-y-3">
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson12')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #f59e0b; color: #1a1a2e;">
              12
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Code Smells e Refatoração</h3>
              <div id="lesson12-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Identificando "maus cheiros" no código</p>
               <p class="mt-2">📌 Técnicas de refatoração: Extract Method, Rename, Move</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson13')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #f59e0b; color: #1a1a2e;">
              13
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Falhas e Regressão</h3>
              <div id="lesson13-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Debugging e análise de falhas</p>
               <p class="mt-2">📌 Testes de regressão para evitar bugs recorrentes</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson14')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #f59e0b; color: #1a1a2e;">
              14
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Consolidação de Conteúdo</h3>
              <div id="lesson14-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>📌 Revisão geral dos conceitos</p>
               <p class="mt-2">📌 Preparação para a apresentação final</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
           <div class="lesson-card p-4 rounded-xl cursor-pointer" style="background: var(--background);" onclick="event.stopPropagation(); toggleLesson('lesson15')">
            <div class="flex items-center gap-3">
             <div class="w-8 h-8 rounded-lg flex items-center justify-center mono text-sm font-bold" style="background: #f59e0b; color: #1a1a2e;">
              15
             </div>
             <div class="flex-1">
              <h3 class="font-semibold" style="color: var(--text);">Apresentação Final</h3>
              <div id="lesson15-details" class="hidden mt-2 text-sm opacity-80" style="color: var(--text);">
               <p>🎉 Showcase dos projetos desenvolvidos</p>
               <p class="mt-2">🏆 Celebração das conquistas!</p>
              </div>
             </div><input type="checkbox" class="w-5 h-5 rounded accent-cyan-400" onclick="event.stopPropagation(); updateProgress(this)">
            </div>
           </div>
          </div>
         </div>
        </div>
       </div>
      </div><!-- Final Node -->
      <div class="animate-slide" style="animation-delay: 0.5s;">
       <div class="relative flex items-center gap-4 md:gap-8">
        <div class="relative z-10 flex-shrink-0 w-12 h-12 rounded-full flex items-center justify-center shadow-lg" style="background: linear-gradient(135deg, var(--primary-action), var(--secondary-action));"><span class="text-2xl">🎓</span>
        </div>
        <div class="flex-1 text-center py-6 rounded-2xl" style="background: linear-gradient(135deg, rgba(99, 102, 241, 0.2), rgba(34, 211, 238, 0.2)); border: 1px solid rgba(99, 102, 241, 0.3);">
         <p class="text-lg font-bold" style="color: var(--text);">Parabéns! Você completou a jornada!</p>
        </div>
       </div>
      </div>
     </div>
    </div>
   </main>
  </div>
  <script>
    const defaultConfig = {
      course_title: '🚀 Jornada da Qualidade de Software',
      course_subtitle: 'Do conceito à entrega',
      background_color: '#0f0f23',
      surface_color: '#1a1a2e',
      text_color: '#e4e4f0',
      primary_action_color: '#6366f1',
      secondary_action_color: '#22d3ee'
    };

    let config = { ...defaultConfig };
    const totalLessons = 15;
    const expandedPhases = new Set();
    const expandedLessons = new Set();

    function togglePhase(phaseId) {
      const content = document.getElementById(`${phaseId}-content`);
      const arrow = document.getElementById(`arrow-${phaseId}`);
      
      if (expandedPhases.has(phaseId)) {
        content.classList.remove('card-expanded');
        content.classList.add('card-collapsed');
        content.style.maxHeight = '0';
        arrow.style.transform = 'rotate(0deg)';
        expandedPhases.delete(phaseId);
      } else {
        content.classList.remove('card-collapsed');
        content.classList.add('card-expanded');
        content.style.maxHeight = content.scrollHeight + 'px';
        arrow.style.transform = 'rotate(180deg)';
        expandedPhases.add(phaseId);
      }
    }

    function toggleLesson(lessonId) {
      const details = document.getElementById(`${lessonId}-details`);
      
      if (expandedLessons.has(lessonId)) {
        details.classList.add('hidden');
        expandedLessons.delete(lessonId);
      } else {
        details.classList.remove('hidden');
        expandedLessons.add(lessonId);
      }
      
      // Recalculate parent phase height
      const phaseContent = details.closest('[id$="-content"]');
      if (phaseContent && expandedPhases.has(phaseContent.id.replace('-content', ''))) {
        phaseContent.style.maxHeight = phaseContent.scrollHeight + 'px';
      }
    }

    function updateProgress() {
      const checkboxes = document.querySelectorAll('input[type="checkbox"]');
      const checked = Array.from(checkboxes).filter(cb => cb.checked).length;
      const percentage = Math.round((checked / totalLessons) * 100);
      
      const progressBar = document.getElementById('progress-bar');
      const progressText = document.getElementById('progress-text');
      
      if (progressBar) progressBar.style.width = `${percentage}%`;
      if (progressText) progressText.textContent = `${percentage}%`;
    }

    async function onConfigChange(newConfig) {
      config = { ...config, ...newConfig };
      
      const titleEl = document.getElementById('course-title');
      const subtitleEl = document.getElementById('course-subtitle');
      
      if (titleEl) titleEl.textContent = config.course_title || defaultConfig.course_title;
      if (subtitleEl) subtitleEl.textContent = config.course_subtitle || defaultConfig.course_subtitle;
      
      // Update CSS variables
      document.documentElement.style.setProperty('--background', config.background_color || defaultConfig.background_color);
      document.documentElement.style.setProperty('--surface', config.surface_color || defaultConfig.surface_color);
      document.documentElement.style.setProperty('--text', config.text_color || defaultConfig.text_color);
      document.documentElement.style.setProperty('--primary-action', config.primary_action_color || defaultConfig.primary_action_color);
      document.documentElement.style.setProperty('--secondary-action', config.secondary_action_color || defaultConfig.secondary_action_color);
    }

    function mapToCapabilities(config) {
      return {
        recolorables: [
          {
            get: () => config.background_color || defaultConfig.background_color,
            set: (value) => { config.background_color = value; window.elementSdk.setConfig({ background_color: value }); }
          },
          {
            get: () => config.surface_color || defaultConfig.surface_color,
            set: (value) => { config.surface_color = value; window.elementSdk.setConfig({ surface_color: value }); }
          },
          {
            get: () => config.text_color || defaultConfig.text_color,
            set: (value) => { config.text_color = value; window.elementSdk.setConfig({ text_color: value }); }
          },
          {
            get: () => config.primary_action_color || defaultConfig.primary_action_color,
            set: (value) => { config.primary_action_color = value; window.elementSdk.setConfig({ primary_action_color: value }); }
          },
          {
            get: () => config.secondary_action_color || defaultConfig.secondary_action_color,
            set: (value) => { config.secondary_action_color = value; window.elementSdk.setConfig({ secondary_action_color: value }); }
          }
        ],
        borderables: [],
        fontEditable: undefined,
        fontSizeable: undefined
      };
    }

    function mapToEditPanelValues(config) {
      return new Map([
        ['course_title', config.course_title || defaultConfig.course_title],
        ['course_subtitle', config.course_subtitle || defaultConfig.course_subtitle]
      ]);
    }

    // Initialize
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }

    // Initial render
    onConfigChange(config);
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9cad33ebe0e4d89c',t:'MTc3MDU3NTQ3NC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
