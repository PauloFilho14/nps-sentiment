# Análise Automática de Sentimento - NPS 

## 📌 Contexto

A UniFECAF recebe mensalmente milhares de feedbacks de alunos por meio de pesquisas NPS.
Este projeto apresenta um protótipo que automatiza a classificação desses comentários,
reduzindo a necessidade de leitura manual e acelerando a identificação de problemas críticos.

## 🎯 Objetivo

Classificar automaticamente feedbacks de alunos em:
- Positivo
- Neutro
- Negativo

Além de sugerir uma ação próxima baseada no sentimento identificado.

## 🛠️ Tecnologia Utilizada

- n8n 
- Google Sheets 
- Google Gemini API 

## 🔄 Fluxo da Solução

1. Leitura dos feedbacks a partir de uma planilha Google Sheets
2. Processamento individual via Gemini com prompt estruturado
3. Extração do sentimento, justificativa e ação sugerida
4. Gravação do resultado em uma planilha de saída

## 🧠 Prompt Utilizado

Você é um analista de experiência do aluno da UniFECAF.

Analise o feedback abaixo e retorne um JSON com:
- sentimento: Positivo, Neutro ou Negativo
- justificativa: explicação curta do motivo
- acao_proxima: ação recomendada para a instituição

Regras:
- Se elogio claro → Positivo
- Se crítica ou problema → Negativo
- Se misto ou indiferente → Neutro

Feedback:
"{{ $json.feedback }}"

Responda APENAS em JSON válido.
Analise o feedback abaixo e responda SOMENTE em JSON válido, sem texto extra.

Formato obrigatório:
{
  "sentimento": "positivo | neutro | negativo",
  "justificativa": "string",
  "acao_proxima": "string"
}

Feedback:
{{ $json.feedback }}

## 📁 Arquivos do Repositório

- `nps_sentiment_unifecaf_n8n.json` → Workflow exportado do n8n
- `README.md` → Documentação do projeto

## 🚀 Observações

Este protótipo pode ser facilmente expandido para:
- Alertas automáticos para feedbacks negativos
- Dashboards de acompanhamento
- Integração com e-mail ou WhatsApp
