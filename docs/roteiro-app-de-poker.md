# Roteiro para criação de um aplicativo de pôquer

## 1. Objetivo

Planejar a criação de um aplicativo de pôquer online, começando por uma versão jogável e evoluindo para funcionalidades de multiplayer, torneios e, somente após validação jurídica e regulatória, uma eventual modalidade com dinheiro real.

Este roteiro é uma referência inicial de produto e execução. Prazos, custos e requisitos devem ser refinados após a definição do escopo, da equipe, das plataformas e do país de operação.

## 2. Princípios do projeto

- **Segurança e integridade do jogo:** as decisões e os resultados de cada mão devem ser calculados e validados no servidor.
- **Evolução por etapas:** validar primeiro a experiência central antes de investir em recursos avançados.
- **Transparência:** registrar ações, resultados e eventos relevantes para investigação de falhas e resolução de disputas.
- **Conformidade antes de monetização:** não oferecer apostas, depósitos, saques ou prêmios resgatáveis sem análise jurídica especializada e confirmação das autorizações aplicáveis.
- **Proteção de dados:** coletar apenas os dados necessários, protegê-los e definir retenção e acesso de acordo com as leis aplicáveis.

## 3. Decisões necessárias antes do desenvolvimento

As decisões abaixo afetam regras, arquitetura, custos e obrigações legais:

1. **Modalidades:** Texas Hold’em, Omaha ou outras variantes.
2. **Formato:** mesas a dinheiro, torneios ou ambos.
3. **Modo econômico:** fichas sem valor monetário e sem saque; ou modalidade com dinheiro real.
4. **Mercado de lançamento:** país e, quando aplicável, regiões em que o serviço estará disponível.
5. **Modelo de receita:** publicidade, assinaturas, itens cosméticos ou rake. O modelo deve ser avaliado juridicamente antes de ser adotado.
6. **Plataformas:** Android, iOS e/ou web.
7. **Público e idade mínima:** política de acesso, verificação de idade e medidas de jogo responsável adequadas ao produto e à jurisdição.

> **Ponto de controle jurídico:** fichas virtuais, prêmios, compras dentro do app e recursos que possam ser convertidos em dinheiro podem ter tratamentos legais diferentes. Consultar advogado especializado nos mercados pretendidos antes de definir a economia do produto ou iniciar qualquer operação com dinheiro real. Este documento não constitui aconselhamento jurídico.

## 4. Fases e cronograma estimado

Os prazos são estimativas iniciais, podem se sobrepor parcialmente e dependem de equipe, escopo, integrações e exigências regulatórias.

| Fase | Estimativa | Resultado esperado |
|---|---:|---|
| 0 — Decisão e validação | 2 a 4 semanas | Escopo, mercado, modelo econômico e riscos definidos |
| 1 — MVP jogável | 1 a 2 meses | Partidas completas e estáveis em mesas pequenas |
| 2 — Multiplayer e torneios | 2 a 3 meses | Lobby, mesas privadas, torneios e ferramentas de integridade |
| 3 — Dinheiro real, se aprovado | 2 a 3 meses ou mais | Fluxos financeiros e controles sujeitos a requisitos legais |
| 4 — Polimento e lançamento | 1 a 2 meses | Produto testado, acessível e preparado para lançamento |

O cronograma total não deve ser tratado como compromisso fechado. A Fase 3 pode exigir autorizações, parceiros e auditorias que alterem significativamente o prazo ou impeçam o lançamento em determinados mercados.

## 5. Fase 0 — Decisão e validação

**Estimativa:** 2 a 4 semanas.

### Atividades

- Escolher as variantes de pôquer e os formatos iniciais.
- Definir se o primeiro lançamento terá apenas fichas virtuais sem saque ou se existe intenção futura de operar com dinheiro real.
- Selecionar país e público-alvo para o lançamento.
- Avaliar com assessoria jurídica as regras aplicáveis ao jogo, à publicidade, às compras, aos prêmios, à privacidade e à proteção de menores.
- Definir modelo de receita compatível com as conclusões jurídicas.
- Identificar requisitos de segurança, privacidade, suporte e operação.
- Preparar uma estimativa de equipe, custos, infraestrutura e cronograma detalhado.

### Entregáveis

- Documento de escopo do MVP.
- Decisões registradas sobre modalidade, mercado, plataforma e economia.
- Matriz inicial de riscos e dependências.
- Parecer ou plano de validação jurídica para cada mercado pretendido.
- Critérios de sucesso do MVP.

### Critério para avançar

Não iniciar funcionalidades financeiras nem anunciar operação com dinheiro real enquanto o modelo e as obrigações aplicáveis não estiverem validados por profissionais qualificados.

## 6. Fase 1 — MVP jogável

**Estimativa:** 1 a 2 meses.

### Escopo do produto

- Motor de Texas Hold’em, caso essa seja a variante escolhida:
  - criação e embaralhamento do baralho;
  - distribuição de cartas e progressão das rodadas;
  - avaliação de mãos, desempate e kicker;
  - ações de check, bet, call, raise, fold e all-in;
  - tratamento correto de side pots e divisão de pote;
  - temporizador de ação.
- Mesas online para heads-up e até seis jogadores.
- Comunicação em tempo real entre cliente e servidor, por exemplo, com WebSocket.
- Reconexão a uma partida em andamento, com recuperação do estado autorizado ao jogador.
- Cadastro e login básicos.
- Saldo de fichas virtuais sem valor resgatável, se esse for o modelo aprovado para o MVP.
- Uma tela de mesa com cartas, assentos, pote, estado da mão e controles de ação.
- Chat simples, com controles básicos contra abuso.

### Diretrizes técnicas iniciais

- O servidor é a autoridade sobre estado da mão, validação de ações, temporizadores e resultado.
- O cliente não deve decidir nem poder alterar cartas, saldo ou resultado.
- Registrar eventos suficientes para depurar partidas e reconstruir o fluxo de uma mão.
- Separar a lógica do jogo da interface para facilitar testes automatizados.
- Proteger sessões e limitar chamadas inválidas ou repetidas.

### Critério de conclusão

Um grupo de até seis pessoas consegue iniciar, concluir e repetir partidas sem divergências nas regras, perda indevida de estado ou bloqueios causados por reconexões comuns. As regras do motor devem ter testes para desempates, all-ins, side pots e divisão de pote.

## 7. Fase 2 — Multiplayer e torneios

**Estimativa:** 2 a 3 meses.

### Funcionalidades

- Lobby com lista de mesas e informações relevantes, como modalidade e quantidade de jogadores.
- Criação de mesa privada com código de convite.
- Torneios Sit & Go para seis ou nove jogadores, com blinds progressivos.
- Histórico de mãos e estatísticas compatíveis com as regras de privacidade e retenção definidas.
- Notificações de turno e início de torneio.
- Ferramentas de moderação e suporte para denúncias.
- Monitoramento de padrões suspeitos de jogo e de abuso de contas.

### Integridade e prevenção de fraude

- Usar sinais como endereço IP, dispositivo, comportamento e padrões de jogo para priorizar análises — não tratar um IP compartilhado como prova isolada de fraude. Redes domésticas, empresariais e móveis podem compartilhar IP.
- Definir procedimentos de revisão, contestação e medidas proporcionais antes de suspender contas.
- Planejar testes e auditoria independente do gerador aleatório antes de qualquer uso em contexto regulado.
- Manter trilhas de auditoria com acesso controlado e proteção contra alterações indevidas.

### Critério de conclusão

Jogadores conseguem encontrar ou criar mesas, participar de torneios, receber notificações e consultar histórico sem comprometer a estabilidade ou a integridade das partidas.

## 8. Fase 3 — Dinheiro real, somente se aprovado

**Estimativa:** 2 a 3 meses ou mais; sujeita a requisitos legais, disponibilidade de parceiros e auditorias.

Esta fase é opcional e não deve começar apenas por estar prevista no cronograma. A decisão de avançar depende de validação jurídica e regulatória para cada mercado, além da capacidade de cumprir requisitos operacionais e de segurança.

### Possíveis frentes de trabalho

- Processo de identificação e verificação de usuários, incluindo KYC e validação de idade, conforme exigido.
- Carteira com depósitos, saques, extratos e reconciliação financeira.
- Integração com provedores de pagamento autorizados e adequados ao mercado.
- Controles contra fraude, lavagem de dinheiro e uso indevido, conforme as obrigações aplicáveis.
- Limites, alertas, relatórios e procedimentos de revisão.
- Registro auditável de mãos, transações e eventos relevantes para resolução de disputas.
- Atendimento especializado para problemas financeiros, disputas e falhas técnicas.
- Controles de jogo responsável, incluindo limites e mecanismos de autoexclusão quando exigidos ou apropriados.
- Avaliações independentes de segurança, jogo e sistemas financeiros, conforme aplicável.

### Critério para avançar ao lançamento

Requisitos jurídicos, autorizações, contratos com provedores, controles operacionais, auditorias e processos de suporte devem estar concluídos e aprovados pelas partes responsáveis. Integrações de pagamento, por si só, não comprovam que a operação é permitida.

## 9. Fase 4 — Polimento e lançamento

**Estimativa:** 1 a 2 meses.

### Atividades

- Finalizar identidade visual, animações, sons e avatares.
- Criar tutorial para iniciantes e mensagens claras sobre regras e ações.
- Realizar testes de carga progressivos, por exemplo, com 500 e 1.000 conexões simultâneas, medindo latência, estabilidade e custo.
- Executar testes de segurança, acessibilidade, compatibilidade e recuperação de falhas.
- Fazer beta fechado com aproximadamente 50 a 100 participantes, com consentimento e canais de feedback.
- Corrigir problemas prioritários e validar os processos de suporte e moderação.
- Planejar lançamento gradual, começando por Android se essa prioridade for confirmada; avaliar iOS e web em seguida.
- Preparar monitoramento, alertas, resposta a incidentes e plano de reversão de versão.

### Critério de conclusão

O produto atende aos critérios de estabilidade e segurança definidos, os problemas críticos do beta foram resolvidos e há capacidade operacional para acompanhar o lançamento.

## 10. Requisitos transversais

### Qualidade

- Testes automatizados das regras e dos cenários-limite do motor.
- Testes de integração para reconexão, torneios e persistência de estado.
- Testes de carga e de falhas de rede.
- Monitoramento de erros, latência e disponibilidade.

### Segurança e privacidade

- Autorização por jogador para qualquer informação específica de uma mão.
- Proteção de credenciais, sessões e dados pessoais.
- Controle de acesso administrativo e registro de ações privilegiadas.
- Política de retenção e exclusão de dados.
- Plano de resposta a incidentes e canal para reportar vulnerabilidades.

### Operação

- Ferramentas internas para suporte e moderação.
- Procedimentos de atendimento, contestação e escalonamento.
- Backups, recuperação e comunicação de indisponibilidades.
- Métricas do produto e da operação, com coleta proporcional e transparente.

## 11. Principais riscos e mitigação

| Risco | Mitigação |
|---|---|
| Incerteza jurídica ou regulatória | Validar mercado e modelo com assessoria especializada antes de investir em funcionalidades financeiras |
| Erros nas regras ou no cálculo de potes | Testes automatizados abrangentes, revisão independente e simulações de cenários-limite |
| Fraude, conluio ou abuso de contas | Monitoramento baseado em múltiplos sinais, revisão humana e processo de contestação |
| Quedas de conexão e dessincronização | Estado autoritativo no servidor, reconexão testada e telemetria |
| Vazamento ou uso indevido de dados | Minimização de coleta, controles de acesso, criptografia e plano de resposta |
| Sobrecarga no lançamento | Testes progressivos, lançamento gradual e monitoramento com capacidade de rollback |
| Dependência de pagamentos ou terceiros | Avaliar fornecedores, contratos, contingências e requisitos antes da integração |

## 12. Próximos passos recomendados

1. Responder às decisões pendentes da Fase 0.
2. Escolher o escopo do MVP e confirmar se ele usará apenas fichas sem valor resgatável.
3. Definir o mercado inicial e solicitar análise jurídica antes de fixar a economia do produto.
4. Estimar equipe, orçamento, arquitetura e cronograma com base nas decisões aprovadas.
5. Criar os critérios de aceite e o plano de testes do motor antes de implementar o multiplayer.
