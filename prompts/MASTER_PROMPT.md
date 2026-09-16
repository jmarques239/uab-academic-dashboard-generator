# MASTER PROMPT: GERADOR DE DASHBOARD ACADÉMICO INTEGRAL RESPONSIVO (UNIVERSIDADE ABERTA)

Atua como Arquiteto de Software Frontend Sénior e Especialista em UI/UX focado em Produtividade Académica.
Recebes em anexo os documentos oficiais PUC (Plano de Unidade Curricular) referentes às disciplinas do semestre da Licenciatura em Engenharia Informática da Universidade Aberta (UAb).

O teu objetivo é processar exaustivamente todos os PUCs fornecidos e gerar, num ÚNICO ficheiro autónomo (.html com CSS puro e Vanilla JavaScript embutidos), um Dashboard Académico de Alto Rendimento com suporte Desktop e Mobile First.

---

### REQUISITOS OBRIGATÓRIOS DE ENGENHARIA E INTERFACE

1. **Stack Tecnológica & Autonomia:**
   - Ficheiro único `.html` (sem frameworks, sem bibliotecas pesadas externas; apenas Google Fonts 'Inter' e 'JetBrains Mono').
   - Modo Dual Light/Dark com alternador no topo e gravação em `localStorage`.
   - Layout híbrido: desktop clássico com sidebar fixa; mobile com header superior fixo, gaveta off-canvas deslizante com overlay e barra de navegação rápida inferior (Bottom Nav) com áreas de toque (touch targets) ergonómicas.

2. **Calendário Matricial Adaptativo (Zero Scroll Horizontal):**
   - Matriz uniforme de 7 colunas (Segunda a Domingo) cobrindo todos os meses do semestre.
   - Design 100% fluido (`width: 100%`, `grid-template-columns: repeat(7, 1fr)` e `min-width: 0` nas células) para que todos os dias da semana fiquem sempre visíveis em qualquer largura de ecrã sem exigir scroll horizontal.
   - **Regra Anti-Ruído:** O calendário só deve exibir barras de eventos para momentos com prazos pontuais e datas limites definitivas (trabalhos, testes, entregas de projeto e provas síncronas). Atividades formativas contínuas ao longo de todo o semestre (como participações contínuas de 0,5v em fóruns) NÃO devem ser renderizadas como barras de 4 meses no calendário.
   - Toggles interativos por UC com as cores oficiais para filtrar a vista do calendário.

3. **Roteiro Semanal de Aprendizagem com Acordeão e Foco Automático:**
   - Organização cronológica rigorosa por Semanas (ex: Semana 0 à Semana 16), com datas explícitas de início e fecho.
   - Cartões individuais por UC contendo:
     * Título claro da etapa;
     * Descrição das leituras e laboratórios (Wireshark, simuladores, IDEs, etc.);
     * Etiquetas visuais (`.topic-tag`) indicando capítulos, conceitos e ferramentas;
     * Linha realçada no rodapé (`.card-highlight-bar`) com destaque de entrega/fecho sumativo, checkpoint formativo ou prazo.
   - **Comportamento de Minimização / Expansão:**
     * Cada semana é um bloco expansível/recolhível com indicador de chevron (`▶`).
     * Ao carregar a página ou selecionar a vista do roteiro, o sistema deteta a data real do utilizador e foca/centra automaticamente a Semana Atual no ecrã (com scroll suave e expansão forçada dessa semana).
     * O utilizador pode recolher/expandir qualquer semana livremente, ficando o estado de cada uma gravado em `localStorage`.
     * Barra de ações rápidas no topo do roteiro com botões para "Centrar na Semana Atual", "Expandir Todas" e "Minimizar Todas".

4. **Interligação Bidirecional de Checkboxes e Métricas de Progresso:**
   - As checkboxes das tarefas no Roteiro Semanal alimentam diretamente a Barra Global do semestre e as Barras Individuais de cada UC na barra lateral.
   - **Sincronização Bidirecional Estrita:** Sempre que uma tarefa com momento sumativo correspondente no Painel de Entregas for assinalada no Roteiro, a linha respetiva no Painel de Entregas fica automaticamente concluída (e vice-versa).
   - O cartão concluído recebe a classe `.is-done` (opacidade reduzida, filtro dessaturado e texto riscado).

5. **Painel Consolidado de Entregas & Critérios:**
   - Tabela auditável contendo: Status (checkbox sincronizada), UC (com badge colorido), Nome Oficial da Atividade, Tipo (Assíncrona / Síncrona / Mista), Data de Início, Data/Hora Limite e Cotação (ex: `5.0v`, `3.0v`, `12.0v`).
   - Filtro dropdown por UC e ordenação ascendente/descendente interativa clicando nos cabeçalhos (UC, nome, tipo, datas e cotação).

6. **Notificações Toast 100% Opacas e Configuráveis:**
   - Sistema de toasts flutuantes não-bloqueantes no topo direito (ou topo central em mobile).
   - **Legibilidade Superior:** Fundo 100% sólido/opaco (sem transparências que se misturem com o texto do fundo), com sombra pronunciada e realce visual.
   - Botão `✕` ou "Entendido" fecha apenas na sessão imediata.
   - Botão "Não voltar a notificar" silencia permanentemente aquele alerta em `localStorage`.
   - Modal de definições (ícone ⚙️) para: ligar/desligar notificações, escolher a antecedência (0, 1, 2, 3, 5 ou 7 dias), repor silenciadas e disparar teste imediato.

7. **Páginas Dedicadas por UC:**
   - Extração estruturada do PUC: Identificação (código e regente), Apresentação, Resultados de Aprendizagem (RA1 a RAn), Metodologia e Ferramentas, Condições Oficiais de Aprovação (regras em cadeia, notas mínimas assíncronas/síncronas e exame/recurso) e Bibliografia Completa (obrigatória e complementar).

---

### INSTRUÇÕES DE EXTRAÇÃO DOS PUCS

1. Extrai todas as UCs presentes nos documentos anexados mantendo as designações oficiais exatas, códigos e nomes dos professores.
2. Analisa cuidadosamente as datas de disponibilização de enunciado e datas/horas limites de submissão de cada PUC.
3. Se o utilizador fornecer datas adicionais na mensagem (ex: datas de provas síncronas globais agendadas por despacho reitoral ou Wiseflow), integra-as com prioridade máxima sobre as informações genéricas do PUC.
4. Idioma obrigatório: Português de Portugal.
5. Formato de resposta: Devolve única e exclusivamente o código integral funcional dentro de um bloco de código ````html ... ````, sem omissões nem comentários do tipo `<!-- código restante aqui -->`.