# Residencial Vitrine — Quiz de Perfil

## Visão Geral
Quiz interativo para qualificar leads do loteamento Residencial Vitrine.
O usuário responde 11 perguntas e recebe um perfil personalizado, depois preenche um formulário que envia os dados para WhatsApp, Google Sheets e e-mail.

## Repositório
- GitHub: https://github.com/glflim/vitrine-quiz
- Site: https://glflim.github.io/vitrine-quiz/

## Arquivos
- `index.html` — toda a aplicação (HTML + CSS + JS em um único arquivo)
- `apps-script.js` — código do Google Apps Script (salvo localmente como referência)
- `docs/` — esta pasta de documentação

---

## Tecnologias Utilizadas
- **HTML/CSS/JS puro** — sem frameworks
- **Google Apps Script** — backend para salvar leads
- **Google Sheets** — planilha de leads
- **Gmail** — notificação por e-mail
- **intl-tel-input v19.5.7** — seletor de telefone internacional
- **GitHub Pages** — hospedagem gratuita

---

## Fluxo do Sistema

1. Usuário acessa o site
2. Responde 11 perguntas do quiz
3. Recebe perfil: **Morador Sonhador** ou **Investidor Visionário**
4. Preenche formulário (Nome, WhatsApp, E-mail) — todos obrigatórios
5. Ao enviar:
   - Abre WhatsApp com mensagem pré-preenchida para Gabriel
   - Dados salvos automaticamente na planilha Google Sheets
   - E-mail de notificação enviado para gabriel.frelich.lima@gmail.com

---

## Google Apps Script

### Script principal (vinculado à planilha)
- **URL:** https://script.google.com/macros/s/AKfycbwbH_ICQedxXn_6M6YyfULQPjacJmxxlw_7xtgaRRubNN55TacTtMsTbOAsjuoxOZGW/exec
- **Projeto:** https://script.google.com/u/0/home/projects/1KWuJI1yUvt9sGrMyfLYPOWN8kOcPpqDLzyBslMzhUew_WCl4OH9aeAKc/edit

### Funções do script
- `doPost(e)` — recebe os dados do formulário, salva na planilha e envia e-mail
- `onSelectionChange(e)` — ao clicar em uma linha na aba "Leads", atualiza a aba "Perfil do Cliente"
- `formatLeadsSheet(sheet)` — formata visualmente a aba Leads
- `aplicarFormatacao()` — aplica formatação manual (rodar uma vez após mudanças)

### Acionador configurado
- Função: `onSelectionChange`
- Origem: Do Planilhas Google
- Tipo: Ao alterar seleção

---

## Google Sheets

### Planilha
- **ID:** 1nRVi8Gnh7BKJxcjMJoI3Xu8UW9ETHWUC43f18Of1gBE
- **Link:** https://docs.google.com/spreadsheets/d/1nRVi8Gnh7BKJxcjMJoI3Xu8UW9ETHWUC43f18Of1gBE/edit

### Abas
- **Leads** — todos os leads recebidos com colunas: Data/Hora, Nome, WhatsApp, E-mail, Perfil, P1 a P11
- **Perfil do Cliente** — criada automaticamente ao clicar em um lead na aba Leads

### Colunas da aba Leads
| Coluna | Conteúdo |
|--------|----------|
| A | Data/Hora |
| B | Nome |
| C | WhatsApp (com bandeira e código do país) |
| D | E-mail |
| E | Perfil (Morador Sonhador / Investidor Visionário) |
| F-P | Respostas P1 a P11 |

---

## Perguntas do Quiz

| # | Categoria | Pergunta |
|---|-----------|----------|
| 1 | Motivação | O que mais te motiva a adquirir um lote? |
| 2 | Prazo | Qual é o seu prazo para usar ou rentabilizar o lote? |
| 3 | Orçamento | Como você prefere organizar o pagamento? |
| 4 | Vizinhança | O que você espera do entorno do seu lote? |
| 5 | Condomínio | O que mais te atrai em um condomínio fechado? |
| 6 | Decisão | Como você tomaria a decisão de comprar um lote? |
| 7 | Tamanho | Qual tamanho de lote faz mais sentido para você? |
| 8 | Sonho | Quando você pensa no Residencial Vitrine, o que imagina? |
| 9 | Experiência | Você já tem experiência com compra de imóveis? |
| 10 | Prioridade | O que é mais importante para você na compra? |
| 11 | Investimento | Qual faixa de investimento está dentro do seu planejamento? |

---

## Faixas de Investimento
- R$ 179.900,00 a R$ 200.000,00
- R$ 200.000,00 a R$ 250.000,00
- R$ 250.000,00 a R$ 300.000,00
- R$ 300.000,00 a R$ 350.000,00

## Condições de Pagamento
- À vista com desconto especial
- Financiamento próprio em até 150x
- Parcelas: 12 · 24 · 36 · 48 · 60 · 72 · 84 · 96 · 108 · 120 · 132 · 150 meses

---

## Perfis de Resultado

### Morador Sonhador
- Critério: 5 ou mais respostas do tipo "m" (morador)
- Cor na planilha: verde

### Investidor Visionário
- Critério: menos de 5 respostas do tipo "m"
- Cor na planilha: azul

---

## Campo de Telefone
- Biblioteca: intl-tel-input v19.5.7
- Botões fixos: Brasil e EUA
- Botão "Outro" abre dropdown com busca por nome do país
- Máscaras implementadas: BR, US, CA, AR, MX, CO, CL, PE, PT, ES, FR, GB, DE, IT, NL, BE, CH, AT, IE, LU, SE, NO, DK, FI, PL, CZ, HU, RO, BG, HR, SK, SI, GR, RU, UA, TR, AU, JP
- Número salvo com bandeira: ex: 🇧🇷 +55 (33) 99830-0030

---

## Contatos
- **WhatsApp do vendedor:** 5533998361707
- **E-mail do vendedor:** gabriel.frelich.lima@gmail.com

---

## Melhorias Futuras Possíveis
- [ ] Adicionar mais perfis de resultado além de Morador/Investidor
- [ ] Dashboard com gráficos na planilha (perfis mais comuns, faixas de investimento)
- [ ] Integração com CRM
- [ ] Versão em inglês/espanhol para clientes internacionais
- [ ] Adicionar foto ou vídeo do empreendimento na tela de resultado
- [ ] Sistema de agendamento de visita direto no quiz
- [ ] Notificação via WhatsApp Business API além do link manual
