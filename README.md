# FERIDAS-TESTE
Este site tem como objetivo oferecer orientações confiáveis, atualizadas e de fácil compreensão sobre a prevenção, avaliação e cuidado com feridas. A plataforma é voltada tanto para profissionais da saúde quanto para estudantes, cuidadores e o público em geral, promovendo informação baseada em boas práticas e evidências científicas.

<!doctype html>
<html lang="pt-BR" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Guia de Primeiros Socorros para Feridas</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    * {
      font-family: 'Nunito', sans-serif;
    }
    .wound-card {
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }
    .wound-card:hover {
      transform: translateY(-4px);
    }
    .dont-item {
      animation: slideIn 0.3s ease-out forwards;
      opacity: 0;
    }
    @keyframes slideIn {
      from {
        opacity: 0;
        transform: translateX(-10px);
      }
      to {
        opacity: 1;
        transform: translateX(0);
      }
    }
    .pulse-warning {
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.7; }
    }
    .back-btn {
      transition: all 0.2s ease;
    }
    .back-btn:hover {
      transform: translateX(-4px);
    }
    .popup-mode-active {
      background: rgba(0, 0, 0, 0.5) !important;
      position: fixed !important;
      top: 0 !important;
      left: 0 !important;
    }
    .popup-container {
      width: 95% !important;
      max-width: 480px !important;
      height: auto !important;
      max-height: 85vh !important;
      position: fixed !important;
      top: 50% !important;
      left: 50% !important;
      transform: translate(-50%, -50%) !important;
      border-radius: 24px !important;
      box-shadow: 0 25px 80px rgba(0,0,0,0.4), 0 0 0 1px rgba(255,255,255,0.1) !important;
      animation: popupAppear 0.4s cubic-bezier(0.34, 1.56, 0.64, 1) !important;
      overflow: hidden !important;
      z-index: 1000 !important;
    }
    .popup-container .overflow-auto {
      max-height: 70vh !important;
    }
    @keyframes popupAppear {
      0% {
        opacity: 0;
        transform: translate(-50%, -50%) scale(0.8);
      }
      100% {
        opacity: 1;
        transform: translate(-50%, -50%) scale(1);
      }
    }
    .popup-toggle-btn {
      position: fixed;
      bottom: 6px;
      right: 6px;
      z-index: 999;
      padding: 12px;
      border-radius: 12px;
      border: none;
      cursor: pointer;
      transition: all 0.3s ease;
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .popup-toggle-btn:hover {
      transform: scale(1.1);
    }
  </style>
  <script src="https://cdn.tailwindcss.com/3.4.17" type="text/javascript"></script>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full"><button id="popup-toggle" class="popup-toggle-btn" onclick="togglePopupMode()" style="background: rgba(255,255,255,0.9); color: #1a1a2e;" title="Modo Pop-up">
   <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" />
   </svg></button>
  <div id="app" class="h-full w-full overflow-auto" style="background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);"><!-- Tela Principal -->
   <div id="main-screen" class="min-h-full p-4 md:p-8">
    <header class="text-center mb-8 pt-4">
     <div class="inline-flex items-center justify-center w-20 h-20 rounded-full mb-4" style="background: linear-gradient(135deg, #e94560 0%, #ff6b6b 100%); box-shadow: 0 8px 32px rgba(233, 69, 96, 0.4);">
      <svg class="w-10 h-10 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
      </svg>
     </div>
     <h1 id="app-title" class="text-3xl md:text-4xl font-extrabold text-white mb-2">Guia de Feridas</h1>
     <p id="app-subtitle" class="text-lg md:text-xl" style="color: #a3bffa;">Identifique o tipo e saiba o que evitar</p>
    </header>
    <div class="max-w-4xl mx-auto">
     <p class="text-center mb-6" style="color: #94a3b8;">Selecione o tipo de ferida para ver orientações:</p>
     <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6"><!-- Corte --> <button onclick="showWound('corte')" class="wound-card rounded-2xl p-6 text-left" style="background: rgba(255,255,255,0.08); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1);">
       <div class="w-14 h-14 rounded-xl flex items-center justify-center mb-4" style="background: linear-gradient(135deg, #ef4444 0%, #f87171 100%);">
        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
       </div><h3 class="text-xl font-bold text-white mb-2">Corte</h3><p class="text-sm" style="color: #94a3b8;">Ferida com bordas definidas causada por objeto cortante</p></button> <!-- Arranhão/Escoriação --> <button onclick="showWound('arranhao')" class="wound-card rounded-2xl p-6 text-left" style="background: rgba(255,255,255,0.08); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1);">
       <div class="w-14 h-14 rounded-xl flex items-center justify-center mb-4" style="background: linear-gradient(135deg, #f59e0b 0%, #fbbf24 100%);">
        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
        </svg>
       </div><h3 class="text-xl font-bold text-white mb-2">Arranhão</h3><p class="text-sm" style="color: #94a3b8;">Escoriação superficial por atrito com superfície áspera</p></button> <!-- Perfuração --> <button onclick="showWound('perfuracao')" class="wound-card rounded-2xl p-6 text-left" style="background: rgba(255,255,255,0.08); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1);">
       <div class="w-14 h-14 rounded-xl flex items-center justify-center mb-4" style="background: linear-gradient(135deg, #8b5cf6 0%, #a78bfa 100%);">
        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><circle cx="12" cy="12" r="3" stroke-width="2" /> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 2v4m0 12v4m10-10h-4M6 12H2" />
        </svg>
       </div><h3 class="text-xl font-bold text-white mb-2">Perfuração</h3><p class="text-sm" style="color: #94a3b8;">Ferida profunda causada por objeto pontiagudo</p></button> <!-- Queimadura --> <button onclick="showWound('queimadura')" class="wound-card rounded-2xl p-6 text-left" style="background: rgba(255,255,255,0.08); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1);">
       <div class="w-14 h-14 rounded-xl flex items-center justify-center mb-4" style="background: linear-gradient(135deg, #dc2626 0%, #f97316 100%);">
        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 18.657A8 8 0 016.343 7.343S7 9 9 10c0-2 .5-5 2.986-7C14 5 16.09 5.777 17.656 7.343A7.975 7.975 0 0120 13a7.975 7.975 0 01-2.343 5.657z" /> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.879 16.121A3 3 0 1012.015 11L11 14H9c0 .768.293 1.536.879 2.121z" />
        </svg>
       </div><h3 class="text-xl font-bold text-white mb-2">Queimadura</h3><p class="text-sm" style="color: #94a3b8;">Lesão por calor, frio, substância química ou eletricidade</p></button> <!-- Contusão --> <button onclick="showWound('contusao')" class="wound-card rounded-2xl p-6 text-left" style="background: rgba(255,255,255,0.08); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1);">
       <div class="w-14 h-14 rounded-xl flex items-center justify-center mb-4" style="background: linear-gradient(135deg, #3b82f6 0%, #60a5fa 100%);">
        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 11.5V14m0-2.5v-6a1.5 1.5 0 113 0m-3 6a1.5 1.5 0 00-3 0v2a7.5 7.5 0 0015 0v-5a1.5 1.5 0 00-3 0m-6-3V11m0-5.5v-1a1.5 1.5 0 013 0v1m0 0V11m0-5.5a1.5 1.5 0 013 0v3m0 0V11" />
        </svg>
       </div><h3 class="text-xl font-bold text-white mb-2">Contusão</h3><p class="text-sm" style="color: #94a3b8;">Hematoma ou "roxo" causado por impacto</p></button> <!-- Mordida --> <button onclick="showWound('mordida')" class="wound-card rounded-2xl p-6 text-left" style="background: rgba(255,255,255,0.08); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1);">
       <div class="w-14 h-14 rounded-xl flex items-center justify-center mb-4" style="background: linear-gradient(135deg, #10b981 0%, #34d399 100%);">
        <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.828 14.828a4 4 0 01-5.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
        </svg>
       </div><h3 class="text-xl font-bold text-white mb-2">Mordida</h3><p class="text-sm" style="color: #94a3b8;">Ferida causada por mordida de animal ou humano</p></button>
     </div>
     <div class="mt-8 p-4 rounded-xl text-center" style="background: rgba(239, 68, 68, 0.15); border: 1px solid rgba(239, 68, 68, 0.3);">
      <p class="text-sm pulse-warning" style="color: #fca5a5;">⚠️ <strong>Atenção:</strong> Este guia é apenas informativo. Em casos graves, procure atendimento médico imediatamente.</p>
     </div>
    </div>
   </div><!-- Tela de Detalhes -->
   <div id="detail-screen" class="min-h-full p-4 md:p-8 hidden">
    <div class="max-w-2xl mx-auto"><button onclick="goBack()" class="back-btn flex items-center gap-2 mb-6 px-4 py-2 rounded-lg text-white" style="background: rgba(255,255,255,0.1);">
      <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg> Voltar </button>
     <div id="wound-detail" class="rounded-2xl p-6 md:p-8" style="background: rgba(255,255,255,0.08); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1);"><!-- Conteúdo dinâmico -->
     </div>
     <div class="mt-6 p-4 rounded-xl" style="background: rgba(59, 130, 246, 0.15); border: 1px solid rgba(59, 130, 246, 0.3);">
      <p class="text-sm text-center" style="color: #93c5fd;">💡 <strong>Dica:</strong> Mantenha a calma e avalie a gravidade antes de agir.</p>
     </div>
    </div>
   </div>
  </div>
  <script>
    let isPopupMode = false;

    function togglePopupMode() {
      isPopupMode = !isPopupMode;
      const app = document.getElementById('app');
      const toggleBtn = document.getElementById('popup-toggle');
      
      if (isPopupMode) {
        app.classList.add('popup-mode-active', 'popup-container');
        app.classList.remove('h-full', 'w-full');
        toggleBtn.style.background = '#8b5cf6';
        toggleBtn.style.color = 'white';
        toggleBtn.title = 'Modo Tela Cheia';
      } else {
        app.classList.remove('popup-mode-active', 'popup-container');
        app.classList.add('h-full', 'w-full');
        toggleBtn.style.background = 'rgba(255,255,255,0.9)';
        toggleBtn.style.color = '#1a1a2e';
        toggleBtn.title = 'Modo Pop-up';
      }
    }

    const defaultConfig = {
      app_title: 'Guia de Feridas',
      subtitle: 'Identifique o tipo e saiba o que evitar',
      primary_color: '#e94560',
      secondary_color: '#1a1a2e',
      text_color: '#ffffff',
      accent_color: '#a3bffa',
      surface_color: '#16213e'
    };

    let config = { ...defaultConfig };

    const woundData = {
      corte: {
        title: 'Corte',
        icon: `<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/></svg>`,
        color: 'linear-gradient(135deg, #ef4444 0%, #f87171 100%)',
        description: 'Ferida com bordas bem definidas, causada por objetos cortantes como facas, vidros ou lâminas.',
        characteristics: [
          'Bordas regulares e bem definidas',
          'Sangramento pode ser intenso',
          'Profundidade variável',
          'Dor localizada na área do corte'
        ],
        dos: [
          { step: '1. Pare o sangramento', action: 'Aplique pressão direta com gaze limpa ou tecido limpo por 5-10 minutos' },
          { step: '2. Lave a ferida', action: 'Use água corrente limpa e sabão neutro com movimentos suaves' },
          { step: '3. Seque com cuidado', action: 'Use gaze estéril ou papel toalha sem deixar fiapos' },
          { step: '4. Desinfete', action: 'Aplique álcool 70% ou antisséptico adequado ao redor (não dentro)' },
          { step: '5. Cubra adequadamente', action: 'Use curativos estéreis ou gaze com fita, mudando a cada 2-3 dias' },
          { step: '6. Monitore', action: 'Observe diariamente por sinais de infecção (vermelhidão, pus, inchaço)' }
        ],
        donts: [
          { text: 'Usar algodão diretamente na ferida', reason: 'Fiapos podem grudar e causar infecção' },
          { text: 'Aplicar pomadas ou cremes sem orientação', reason: 'Pode interferir na cicatrização' },
          { text: 'Tentar juntar as bordas de cortes profundos', reason: 'Requer avaliação e sutura profissional' },
          { text: 'Usar água oxigenada ou álcool puro', reason: 'Danifica os tecidos em recuperação' },
          { text: 'Remover objetos presos na ferida', reason: 'Pode causar hemorragia grave' },
          { text: 'Ignorar sinais de infecção', reason: 'Vermelhidão, pus ou febre exigem médico' }
        ],
        emergency: 'Procure atendimento se: sangramento não para em 10 min, corte muito profundo ou em articulações.'
      },
      arranhao: {
        title: 'Arranhão / Escoriação',
        icon: `<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>`,
        color: 'linear-gradient(135deg, #f59e0b 0%, #fbbf24 100%)',
        description: 'Lesão superficial na pele causada por atrito com superfícies ásperas, como asfalto ou concreto.',
        characteristics: [
          'Afeta camadas superficiais da pele',
          'Área avermelhada e ardente',
          'Pode ter pequenos pontos de sangramento',
          'Comum em joelhos, cotovelos e palmas'
        ],
        dos: [
          { step: '1. Limpe imediatamente', action: 'Use água corrente morna e sabão suave para remover terra e sujeira' },
          { step: '2. Remova resíduos', action: 'Com pinça esterilizada, remova cuidadosamente pedaços de terra incrustados' },
          { step: '3. Seque bem', action: 'Use gaze estéril, sem deixar umidade que favoreça infecção' },
          { step: '4. Aplique antisséptico', action: 'Use álcool 70% ou solução antisséptica adequada' },
          { step: '5. Use pomada cicatrizante', action: 'Aplique pomada com antibiótico se recomendado pelo farmacêutico' },
          { step: '6. Deixe respirar', action: 'Não cubra se possível, ou use bandagem que deixe passar ar' },
          { step: '7. Hidrate a pele', action: 'Após cicatrização inicial, use hidratante para evitar manchas' }
        ],
        donts: [
          { text: 'Esfregar a ferida com força', reason: 'Aumenta o dano aos tecidos' },
          { text: 'Deixar resíduos de terra ou sujeira', reason: 'Alto risco de infecção e tétano' },
          { text: 'Cobrir com curativos apertados', reason: 'A ferida precisa "respirar" para cicatrizar' },
          { text: 'Coçar ou arrancar casquinhas', reason: 'Atrasa a cicatrização e pode deixar marca' },
          { text: 'Usar merthiolate ou mercúrio', reason: 'Produtos obsoletos e potencialmente tóxicos' },
          { text: 'Expor ao sol sem proteção', reason: 'Pode causar manchas permanentes' }
        ],
        emergency: 'Procure atendimento se: ferida muito extensa, com terra profundamente incrustada ou sinais de infecção.'
      },
      perfuracao: {
        title: 'Perfuração',
        icon: `<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><circle cx="12" cy="12" r="3" stroke-width="2"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 2v4m0 12v4m10-10h-4M6 12H2"/></svg>`,
        color: 'linear-gradient(135deg, #8b5cf6 0%, #a78bfa 100%)',
        description: 'Ferida profunda e estreita causada por objetos pontiagudos como pregos, espinhos ou agulhas.',
        characteristics: [
          'Entrada pequena mas profundidade significativa',
          'Sangramento externo pode ser mínimo',
          'Alto risco de infecção interna',
          'Dor intensa e pontual'
        ],
        dos: [
          { step: '1. Procure orientação médica', action: 'Feridas perfurantes SEMPRE exigem avaliação profissional' },
          { step: '2. Se objeto pequeno saiu', action: 'Deixe a ferida sangrar naturalmente por alguns segundos' },
          { step: '3. Lave delicadamente', action: 'Use água corrente morna sem apertar ou espremer a ferida' },
          { step: '4. Seque cuidadosamente', action: 'Use gaze estéril com movimentos suaves' },
          { step: '5. Aplique antisséptico', action: 'Use álcool 70% nas bordas, deixando sangrar levemente' },
          { step: '6. Cubra com bandagem', action: 'Use curativo estéril que permita drenagem' },
          { step: '7. Verifique vacinação', action: 'Confirme se a vacina antitetânica está em dia (a cada 10 anos)' },
          { step: '8. Monitore infecção', action: 'Observe febre, aumento de dor, inchaço, pus ou vermelhidão' }
        ],
        donts: [
          { text: 'NUNCA remover objetos grandes encravados', reason: 'Pode causar hemorragia fatal - aguarde socorro' },
          { text: 'Apertar para "sair o sangue ruim"', reason: 'Não funciona e pode piorar a lesão' },
          { text: 'Subestimar por parecer pequena', reason: 'Perfurações são propensas a infecções graves' },
          { text: 'Fechar a ferida completamente', reason: 'Pode aprisionar bactérias dentro' },
          { text: 'Ignorar necessidade de vacina antitetânica', reason: 'Pregos e objetos sujos transmitem tétano' },
          { text: 'Aplicar calor na área', reason: 'Pode aumentar sangramento e inchaço' }
        ],
        emergency: 'SEMPRE procure médico para perfurações, especialmente por objetos enferrujados ou sujos!'
      },
      queimadura: {
        title: 'Queimadura',
        icon: `<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 18.657A8 8 0 016.343 7.343S7 9 9 10c0-2 .5-5 2.986-7C14 5 16.09 5.777 17.656 7.343A7.975 7.975 0 0120 13a7.975 7.975 0 01-2.343 5.657z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.879 16.121A3 3 0 1012.015 11L11 14H9c0 .768.293 1.536.879 2.121z"/></svg>`,
        color: 'linear-gradient(135deg, #dc2626 0%, #f97316 100%)',
        description: 'Lesão causada por calor, frio extremo, substâncias químicas, eletricidade ou radiação.',
        characteristics: [
          '1º grau: vermelhidão e dor',
          '2º grau: bolhas com líquido',
          '3º grau: pele esbranquiçada ou carbonizada',
          'Pode afetar múltiplas camadas da pele'
        ],
        dos: [
          { step: '1. Afaste do calor', action: 'Remova a pessoa da fonte de calor imediatamente' },
          { step: '2. Esfrie imediatamente', action: 'Use água morna (não fria) corrente por 10-15 minutos' },
          { step: '3. Remova adornos', action: 'Tire anéis, pulseiras antes do inchaço aumentar' },
          { step: '4. Lave delicadamente', action: 'Com água e sabão suave, sem esfregar a área' },
          { step: '5. Seque suavemente', action: 'Use pano limpo com movimentos leves' },
          { step: '6. Use pomada específica', action: 'Aplique pomada para queimaduras recomendada por médico' },
          { step: '7. Cubra se necessário', action: 'Use gaze estéril ou bandagem que deixe passar ar' },
          { step: '8. Tome analgésicos', action: 'Dipirona ou ibuprofeno para alivio da dor (conforme orientado)' }
        ],
        donts: [
          { text: 'NUNCA estourar bolhas', reason: 'Protegem contra infecção - deixe intactas' },
          { text: 'Aplicar gelo diretamente', reason: 'Causa queimadura por frio adicional' },
          { text: 'Usar manteiga, pasta de dente ou clara de ovo', reason: 'Mitos perigosos que causam infecção' },
          { text: 'Remover roupas grudadas na pele', reason: 'Pode arrancar tecido junto - corte ao redor' },
          { text: 'Cobrir com algodão ou tecidos felpudos', reason: 'Fiapos grudam na ferida' },
          { text: 'Expor a queimadura ao sol', reason: 'Área fica extremamente sensível por meses' }
        ],
        emergency: 'Procure emergência se: queimadura maior que a palma da mão, no rosto/mãos/genitais, ou de 3º grau.'
      },
      contusao: {
        title: 'Contusão (Hematoma)',
        icon: `<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 11.5V14m0-2.5v-6a1.5 1.5 0 113 0m-3 6a1.5 1.5 0 00-3 0v2a7.5 7.5 0 0015 0v-5a1.5 1.5 0 00-3 0m-6-3V11m0-5.5v-1a1.5 1.5 0 013 0v1m0 0V11m0-5.5a1.5 1.5 0 013 0v3m0 0V11"/></svg>`,
        color: 'linear-gradient(135deg, #3b82f6 0%, #60a5fa 100%)',
        description: 'Sangramento interno sob a pele causado por impacto, resultando em manchas roxas ou azuladas.',
        characteristics: [
          'Mancha que muda de cor (roxo → verde → amarelo)',
          'Inchaço e sensibilidade local',
          'Dor ao toque',
          'Geralmente cicatriza sozinha em 2-3 semanas'
        ],
        dos: [
          { step: '1. Nas primeiras 48 horas: Gelo', action: 'Aplique gelo (20 min cada 3-4 horas) para reduzir inchaço' },
          { step: '2. Eleve a área', action: 'Mantenha a região acima do nível do coração quando possível' },
          { step: '3. Comprima suavemente', action: 'Use bandagem elástica sem apertar demais a circulação' },
          { step: '4. Repouso', action: 'Evite atividades que aumentem o sangramento' },
          { step: '5. Após 48 horas: Calor', action: 'Compressa morna por 15 minutos para melhorar circulação' },
          { step: '6. Massagem leve', action: 'Após 3-4 dias, massageie suavemente ao redor da área' },
          { step: '7. Medicação se necessário', action: 'Dipirona para dor (conforme posologia, não ultrapasse 3-4g/dia)' },
          { step: '8. Protetor solar', action: 'Quando cicatrizar, use protetor solar para evitar manchas' }
        ],
        donts: [
          { text: 'Aplicar calor nas primeiras 48 horas', reason: 'Aumenta o sangramento interno' },
          { text: 'Massagear a área afetada imediatamente', reason: 'Pode espalhar o hematoma' },
          { text: 'Ignorar hematomas que surgem sem trauma', reason: 'Pode indicar problemas de coagulação' },
          { text: 'Fazer atividade intensa com a área', reason: 'Pode piorar a lesão' },
          { text: 'Tomar aspirina ou ibuprofeno logo após', reason: 'Esses medicamentos afinam o sangue' },
          { text: 'Furar ou tentar drenar o hematoma', reason: 'Risco grave de infecção' }
        ],
        emergency: 'Procure médico se: hematoma muito grande, em expansão, dor intensa, ou após trauma na cabeça.'
      },
      mordida: {
        title: 'Mordida',
        icon: `<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.828 14.828a4 4 0 01-5.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>`,
        color: 'linear-gradient(135deg, #10b981 0%, #34d399 100%)',
        description: 'Ferida causada por mordida de animal (cão, gato, etc.) ou humano, com alto risco de infecção.',
        characteristics: [
          'Marcas de dentes visíveis',
          'Pode combinar perfuração e laceração',
          'Alto risco de infecção bacteriana',
          'Inchaço e vermelhidão são comuns'
        ],
        dos: [
          { step: '1. Procure atendimento médico', action: 'Qualquer mordida de animal deve ser avaliada por médico' },
          { step: '2. Lave imediatamente', action: 'Com água corrente morna e sabão por pelo menos 5 minutos' },
          { step: '3. Deixe sangrar naturalmente', action: 'Sangramento ajuda a expelir bactérias da ferida' },
          { step: '4. Aplique antisséptico', action: 'Use álcool 70%, água oxigenada ou povidine iodo' },
          { step: '5. Cubra com curativo', action: 'Use gaze estéril, deixando aberto para cicatrização' },
          { step: '6. Teste raiva do animal', action: 'Identifique o animal e investigue se tem vacinação antirrábica' },
          { step: '7. Tome antibióticos', action: 'Médico pode prescrever (amoxicilina com clavulanato é comum)' },
          { step: '8. Verifique vacinação', action: 'Confirme vacina contra tétano (a cada 10 anos) e antirrábica se necessário' }
        ],
        donts: [
          { text: 'Ignorar mordidas de gatos', reason: 'Dentes finos causam infecções profundas graves' },
          { text: 'Fechar a ferida com pontos em casa', reason: 'Mordidas frequentemente precisam ficar abertas' },
          { text: 'Dispensar avaliação médica', reason: 'Pode precisar de antibióticos e vacinas' },
          { text: 'Deixar de identificar o animal', reason: 'Importante para avaliar risco de raiva' },
          { text: 'Aplicar torniquete', reason: 'Mordidas raramente necessitam - pode causar dano' },
          { text: 'Subestimar mordidas humanas', reason: 'A boca humana tem muitas bactérias perigosas' }
        ],
        emergency: 'SEMPRE procure médico após mordidas de animais! Vacina antirrábica pode ser necessária.'
      }
    };

    function showWound(type) {
      const data = woundData[type];
      const mainScreen = document.getElementById('main-screen');
      const detailScreen = document.getElementById('detail-screen');
      const detailContent = document.getElementById('wound-detail');

      let dontsHtml = data.donts.map((item, index) => `
        <div class="dont-item flex gap-3 p-4 rounded-xl mb-3" style="background: rgba(239, 68, 68, 0.1); border-left: 3px solid #ef4444; animation-delay: ${index * 0.1}s;">
          <div class="flex-shrink-0 w-8 h-8 rounded-full flex items-center justify-center" style="background: rgba(239, 68, 68, 0.2);">
            <svg class="w-5 h-5" style="color: #f87171;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
            </svg>
          </div>
          <div>
            <p class="font-semibold text-white">${item.text}</p>
            <p class="text-sm mt-1" style="color: #94a3b8;">${item.reason}</p>
          </div>
        </div>
      `).join('');

      let dosHtml = data.dos.map((item, index) => `
        <div class="dont-item flex gap-3 p-4 rounded-xl mb-3" style="background: rgba(16, 185, 129, 0.1); border-left: 3px solid #10b981; animation-delay: ${index * 0.05}s;">
          <div class="flex-shrink-0 w-8 h-8 rounded-full flex items-center justify-center font-bold" style="background: rgba(16, 185, 129, 0.3); color: #34d399;">
            ${item.step.split('.')[0]}
          </div>
          <div>
            <p class="font-semibold text-white">${item.step.split(': ')[1]}</p>
            <p class="text-sm mt-1" style="color: #94a3b8;">${item.action}</p>
          </div>
        </div>
      `).join('');

      let characteristicsHtml = data.characteristics.map(char => `
        <li class="flex items-start gap-2">
          <span style="color: #34d399;">✓</span>
          <span>${char}</span>
        </li>
      `).join('');

      detailContent.innerHTML = `
        <div class="flex items-center gap-4 mb-6">
          <div class="w-16 h-16 rounded-xl flex items-center justify-center" style="background: ${data.color};">
            ${data.icon}
          </div>
          <div>
            <h2 class="text-2xl md:text-3xl font-bold text-white">${data.title}</h2>
          </div>
        </div>

        <p class="text-lg mb-6" style="color: #cbd5e1;">${data.description}</p>

        <div class="mb-6 p-4 rounded-xl" style="background: rgba(16, 185, 129, 0.1); border: 1px solid rgba(16, 185, 129, 0.3);">
          <h3 class="font-bold text-white mb-3 flex items-center gap-2">
            <span style="color: #34d399;">🔍</span> Como identificar:
          </h3>
          <ul class="space-y-2" style="color: #a3bffa;">
            ${characteristicsHtml}
          </ul>
        </div>

        <div class="mb-6 p-4 rounded-xl" style="background: rgba(34, 197, 94, 0.1); border: 1px solid rgba(34, 197, 94, 0.3);">
          <h3 class="font-bold text-xl text-white mb-4 flex items-center gap-2">
            <span class="w-8 h-8 rounded-full flex items-center justify-center" style="background: rgba(34, 197, 94, 0.2);">
              <svg class="w-5 h-5" style="color: #86efac;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
              </svg>
            </span>
            Como Tratar:
          </h3>
          ${dosHtml}
        </div>

        <div class="mb-6">
          <h3 class="font-bold text-xl text-white mb-4 flex items-center gap-2">
            <span class="w-8 h-8 rounded-full flex items-center justify-center" style="background: rgba(239, 68, 68, 0.2);">
              <svg class="w-5 h-5" style="color: #f87171;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/>
              </svg>
            </span>
            O que NÃO fazer:
          </h3>
          ${dontsHtml}
        </div>

        <div class="p-4 rounded-xl" style="background: linear-gradient(135deg, rgba(220, 38, 38, 0.2) 0%, rgba(239, 68, 68, 0.1) 100%); border: 1px solid rgba(239, 68, 68, 0.4);">
          <p class="font-semibold text-white flex items-start gap-2">
            <span class="text-2xl">🚨</span>
            <span>${data.emergency}</span>
          </p>
        </div>
      `;

      mainScreen.classList.add('hidden');
      detailScreen.classList.remove('hidden');
      window.scrollTo(0, 0);
    }

    function goBack() {
      const mainScreen = document.getElementById('main-screen');
      const detailScreen = document.getElementById('detail-screen');
      
      detailScreen.classList.add('hidden');
      mainScreen.classList.remove('hidden');
      window.scrollTo(0, 0);
    }

    async function onConfigChange(newConfig) {
      config = { ...defaultConfig, ...newConfig };
      
      const titleEl = document.getElementById('app-title');
      const subtitleEl = document.getElementById('app-subtitle');
      
      if (titleEl) {
        titleEl.textContent = config.app_title || defaultConfig.app_title;
        titleEl.style.color = config.text_color || defaultConfig.text_color;
      }
      
      if (subtitleEl) {
        subtitleEl.textContent = config.subtitle || defaultConfig.subtitle;
        subtitleEl.style.color = config.accent_color || defaultConfig.accent_color;
      }
    }

    function mapToCapabilities(config) {
      return {
        recolorables: [
          {
            get: () => config.secondary_color || defaultConfig.secondary_color,
            set: (value) => {
              config.secondary_color = value;
              window.elementSdk.setConfig({ secondary_color: value });
            }
          },
          {
            get: () => config.surface_color || defaultConfig.surface_color,
            set: (value) => {
              config.surface_color = value;
              window.elementSdk.setConfig({ surface_color: value });
            }
          },
          {
            get: () => config.text_color || defaultConfig.text_color,
            set: (value) => {
              config.text_color = value;
              window.elementSdk.setConfig({ text_color: value });
            }
          },
          {
            get: () => config.primary_color || defaultConfig.primary_color,
            set: (value) => {
              config.primary_color = value;
              window.elementSdk.setConfig({ primary_color: value });
            }
          },
          {
            get: () => config.accent_color || defaultConfig.accent_color,
            set: (value) => {
              config.accent_color = value;
              window.elementSdk.setConfig({ accent_color: value });
            }
          }
        ],
        borderables: [],
        fontEditable: undefined,
        fontSizeable: undefined
      };
    }

    function mapToEditPanelValues(config) {
      return new Map([
        ['app_title', config.app_title || defaultConfig.app_title],
        ['subtitle', config.subtitle || defaultConfig.subtitle]
      ]);
    }

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9ced7d73b6d2ba11',t:'MTc3MTI0OTU3NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
