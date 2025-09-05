# analise_de_sentimentos_azureAI
Repositório DIO — Análise de Sentimentos com Language Studio no Azure AI

Tecnologia utilizada: [![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/)

## Visão geral
Este repositório apresenta uma prova de conceito de Análise de Sentimentos utilizando o Language Studio do Azure AI. A ideia é usar um texto curto (um e-mail fictício para um restaurante) para observar como o serviço classifica o sentimento geral do documento e o sentimento por sentença, e tirar lições sobre potencial de uso em escala.

## Texto aplicado no "Analyze sentiment and opinions"
FICTÍCIO — Trata-se de um e-mail enviado ao restaurante do Joe para relatar a experiência. O tom geral é de avaliação mista, com equilíbrio, profissional e cordial, mas apontando leves frustrações. A intenção é que a IA forneça esse feedback de forma objetiva.

Hi Joe’s team,

I visited last night and wanted to share a brief review. The staff were welcoming and the ambiance was cozy. My grilled salmon was flavorful, but it arrived lukewarm and the wait between courses was longer than expected. Overall, I appreciated the friendly service and fair prices; with quicker pacing and hotter plates, the experience would be excellent.

Best regards, Daniel

## Resultados
- Sentimento do documento: mixed
- Confidence scores (documento):
  - Positivo: 0.75
  - Neutro: 0.05
  - Negativo: 0.20
- Exemplos de sentimento por sentença (com base no JSON fornecido):
  - Uma sentença classificada como neutra com alta confiança (neutro: 0.98).
  - A despedida “Best regards, Daniel” foi classificada como positiva (positivo: 0.94).
  - Observação: o recorte de JSON enviado tem trechos omitidos, então não listamos cada sentença com seus respectivos scores aqui. Se desejar, posso incorporar o JSON completo para um quadro detalhado por sentença.

Imagens do Language Studio (capturas de tela):

<img width="284" height="202" alt="Visão geral do sentimento do documento" src="https://github.com/user-attachments/assets/61cd056c-55b2-4ef1-bf5d-67967005b230" />
<img width="258" height="283" alt="Distribuição de sentimentos" src="https://github.com/user-attachments/assets/95a19151-e9f3-4f73-8fec-048eca92a80b" />
<img width="512" height="285" alt="Confiança por classe de sentimento" src="https://github.com/user-attachments/assets/51817763-7a3f-4b28-b63c-4b0de2b03e8c" />
<img width="710" height="333" alt="Detalhe por sentença (exemplo 1)" src="https://github.com/user-attachments/assets/11c5ddfd-35d1-4fee-8555-c8b5d5090695" />
<img width="809" height="417" alt="Detalhe por sentença (exemplo 2)" src="https://github.com/user-attachments/assets/05aed731-7472-4a9e-ab25-6f349462fa1c" />
<img width="772" height="373" alt="Insights de opinião/aspectos" src="https://github.com/user-attachments/assets/b6a8c563-86c3-451f-afbf-abb2ec036fe4" />
<img width="675" height="345" alt="Resumo do documento" src="https://github.com/user-attachments/assets/24da160a-86ed-4c7d-934a-d97ffde4a602" />
<img width="286" height="293" alt="Classificação final" src="https://github.com/user-attachments/assets/254587f1-85a6-4163-a5ea-9b9d41479207" />

Metadado do modelo (conforme JSON):
- modelVersion: 2025-01-01

## Resumo dos insights
- O documento foi classificado como mixed, mas com viés positivo forte (0.75 positivo vs. 0.20 negativo). O neutro ficou marginal (0.05).
- Há evidência de polaridade mista dentro de frases que combinam elogios e críticas (“flavorful, but lukewarm...”), padrão comum em reviews reais. Isso ajuda a explicar a classificação global como mista.
- A despedida cordial foi reconhecida como positiva (0.94), reforçando o tom respeitoso e profissional do texto.
- Mesmo com poucas sentenças, o serviço capturou bem o equilíbrio entre elogios (staff, ambiente, preço) e pontos de atrito (tempo de espera, temperatura do prato).

## Como reproduzir rapidamente
1. Acesse o Language Studio do Azure AI em “Analyze sentiment and opinions” e cole o texto acima.
2. Execute a análise e salve:
   - A classificação de sentimento do documento
   - As classificações por sentença (com confidence scores)
   - Exportações/prints que preferir
3. Opcional: exporte o resultado em JSON e adicione à pasta do projeto para auditoria e versionamento.

## Considerações
- Valor prático: Ainda que seja um exemplo curto, a ferramenta mostra maturidade para:
  - Consolidar sentimento geral de reviews
  - Capturar nuances dentro da mesma sentença (ex.: “bom, porém…”)
  - Oferecer scores quantitativos úteis para comparar períodos, produtos, lojas ou campanhas
- Escalabilidade: Em grande escala (milhares/milhões de avaliações), é possível:
  - Monitorar tendência de sentimento ao longo do tempo (semanas/meses)
  - Identificar picos de negatividade e correlacionar com eventos operacionais
  - Priorizar melhorias com base na frequência de aspectos negativos (ex.: “tempo de espera”, “temperatura do prato”)
- Qualidade dos dados: Resultados robustos dependem de:
  - Amostras representativas (evitar viés por poucos textos)
  - Limpeza e padronização (idioma, encoding, remoção de duplicados)
  - Contexto e domínio (gírias, regionalismos, ironias podem gerar classificações “mixed”)
- Interpretação: Um score positivo alto junto a um negativo não desprezível (0.20) indica que há oportunidade clara de melhoria. Nesse caso, ajustes operacionais simples (pacing do serviço, manter pratos mais quentes) provavelmente elevariam a satisfação rapidamente.





