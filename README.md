# DIO-LAB
Trabalho de conclusão DIO automação com N8N
# 📚 Automação de Lembretes Semanais de Aulas com n8n

## 1. Apresentação do Projeto

Este projeto tem como objetivo demonstrar o planejamento de uma automação utilizando prompts bem estruturados e a ferramenta n8n. A proposta consiste em desenvolver um sistema capaz de consultar uma lista de aulas semanais, identificar os próximos horários e preparar lembretes automáticos para ajudar o estudante a organizar sua rotina.

A automação utiliza o Google Sheets como fonte de dados e prevê o envio de notificações pelo WhatsApp. Para facilitar os testes iniciais, o projeto também conta com um modo de simulação, que permite visualizar as mensagens sem realizar envios reais.

## 2. Objetivo

Criar um fluxo de automação que consulte os horários das aulas e prepare um lembrete com 24 horas de antecedência.

Os principais objetivos são:

- Automatizar a consulta dos horários das aulas.
- Identificar as próximas ocorrências semanais.
- Preparar mensagens personalizadas com as informações de cada aula.
- Reduzir o risco de esquecer compromissos acadêmicos.
- Demonstrar como prompts claros podem orientar a construção de workflows no n8n.

## 3. Ferramentas Utilizadas

**n8n:** plataforma de automação responsável por organizar e executar as etapas do fluxo.

**Google Sheets:** ferramenta utilizada para armazenar os dados das aulas, incluindo nome, dia da semana, horário, local e situação do cadastro.

**WhatsApp:** canal planejado para o envio dos lembretes. O envio real depende de uma integração compatível e de suas respectivas configurações.

**Inteligência Artificial:** utilizada como apoio para estruturar o prompt, planejar a lógica da automação e documentar o workflow.

## 4. Funcionamento da Automação

O funcionamento planejado segue as seguintes etapas:

1. O n8n inicia a execução em um horário programado.
2. O sistema consulta a planilha que contém as aulas cadastradas.
3. Os registros inativos ou inválidos são desconsiderados.
4. O fluxo calcula a próxima ocorrência de cada aula, considerando o dia da semana e o horário.
5. O sistema identifica quando o lembrete deve ser preparado, com antecedência de 24 horas.
6. Uma mensagem personalizada é gerada com o nome da aula, o horário e o local ou link.
7. Na versão completa, a mensagem é enviada pelo WhatsApp.
8. O resultado do processamento é registrado para facilitar o acompanhamento e evitar notificações duplicadas.

O fluxo deverá considerar o fuso horário `America/Sao_Paulo` para evitar erros nos cálculos de datas e horários.

## 5. Exemplo de Dados

A planilha poderá conter as seguintes colunas:

| nome_aula | dia_semana | horario | local_link | telefone | ativo |
|---|---|---|---|---|---|
| Banco de Dados | Segunda | 19:00 | Sala 204 | 5511999999999 | Sim |
| Programação Web | Quarta | 20:00 | Online | 5511999999999 | Sim |
| Redes | Sexta | 18:00 | Sala 102 | 5511999999999 | Não |

Os dados apresentados são fictícios e servem apenas para demonstrar a estrutura da planilha.

## 6. Exemplo de Mensagem

A mensagem preparada pela automação poderá seguir este modelo:

> 📚 Lembrete de aula!
>
> Amanhã você tem aula de Banco de Dados, às 19:00.
>
> 📍 Local: Sala 204.
>
> Organize-se para não perder o horário!

As informações serão preenchidas dinamicamente de acordo com os dados cadastrados.

## 7. Prompt Utilizado no Planejamento

O prompt é a instrução fornecida à inteligência artificial para orientar a construção da automação.

**Prompt final:**

"Atue como especialista em n8n e me ajude a planejar uma automação de lembretes semanais de aulas.

O sistema deverá consultar uma planilha do Google Sheets contendo o nome da aula, o dia da semana, o horário, o local ou link, o telefone do destinatário e a situação do cadastro.

O n8n deverá verificar diariamente as próximas aulas e preparar lembretes com 24 horas de antecedência, considerando o fuso horário America/Sao_Paulo.

A automação deverá ignorar registros inativos ou inválidos, gerar mensagens personalizadas e prever mecanismos para evitar notificações duplicadas.

Explique como configurar cada nó, incluindo o agendamento, a leitura dos dados, o cálculo das próximas ocorrências e a integração com o WhatsApp.

Apresente um tutorial passo a passo, exemplos de entradas e saídas, um roteiro de testes e um workflow JSON importável. Não invente credenciais e identifique as integrações que precisam de configuração manual.

Comece com uma versão de simulação que não envie mensagens reais e explique como evoluir para uma implementação completa."

## 8. Estrutura do Workflow

A estrutura planejada para o n8n é:

**Schedule Trigger → Google Sheets → IF/Code → Preparação da mensagem → WhatsApp**

- **Schedule Trigger:** inicia a execução automaticamente.
- **Google Sheets:** consulta os dados cadastrados.
- **IF/Code:** verifica os registros e calcula as próximas aulas.
- **Preparação da mensagem:** monta o texto personalizado.
- **WhatsApp:** envia a notificação após a configuração da integração.

Na versão de demonstração, os dados podem ser definidos diretamente no nó Code. A leitura real da planilha e o envio pelo WhatsApp são etapas de integração posteriores.

## 9. Testes e Validação

Para validar a proposta, recomenda-se realizar os seguintes testes:

- Verificar se os dados das aulas são processados corretamente.
- Confirmar se registros inativos são ignorados.
- Conferir o cálculo da próxima ocorrência semanal.
- Validar a antecedência de 24 horas.
- Verificar o conteúdo das mensagens geradas.
- Testar horários próximos à mudança de dia e de semana.
- Confirmar que a versão completa não envia notificações duplicadas.
- Simular falhas de leitura e de envio para verificar o tratamento de erros.

Os testes devem ser executados antes de utilizar a automação em uma rotina real.

## 10. Limitações da Versão de Demonstração

A versão inicial tem finalidade educacional e demonstrativa. O workflow de exemplo utiliza dados definidos diretamente no código e prepara mensagens simuladas.

Portanto, essa versão ainda não realiza a leitura efetiva do Google Sheets, não executa o agendamento automático completo e não envia mensagens reais pelo WhatsApp.

Para implementar essas funcionalidades, será necessário configurar os nós correspondentes, as credenciais e a persistência dos registros de envio.

O envio pelo WhatsApp também depende dos requisitos do serviço ou provedor escolhido.

## 11. Possíveis Melhorias

Entre as melhorias futuras, destacam-se:

- Integrar efetivamente o Google Sheets ao workflow.
- Configurar a execução automática pelo Schedule Trigger.
- Implementar o controle persistente de notificações enviadas.
- Adicionar registros de erros e novas tentativas de envio.
- Integrar uma API compatível com o WhatsApp.
- Permitir a atualização e inclusão de novas aulas sem modificar o código.
- Criar relatórios de execução e acompanhamento dos lembretes.

## 12. Conclusão

O projeto demonstra como um prompt bem estruturado pode transformar uma necessidade cotidiana em um planejamento de automação. Ao definir claramente o objetivo, os dados de entrada, as regras de funcionamento e o resultado esperado, torna-se mais fácil orientar uma inteligência artificial na construção de um workflow.

A proposta de lembretes semanais de aulas apresenta uma aplicação prática do n8n, integrando organização de dados, processamento de informações e preparação de notificações. A versão inicial serve como base para testes e aprendizado, podendo evoluir para uma solução completa com integrações reais.

## 13. Referência

Laboratório da Digital Innovation One (DIO):

https://github.com/digitalinnovationone/dio-lab-assistente-investimentos-rpa-n8n

Projeto desenvolvido para fins educacionais, com foco no planejamento de automações utilizando prompts estruturados e n8n.
