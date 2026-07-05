# MVP Machine-Learning
Repositório dedicado ao desenvolvimento do MVP do Sprint Machine Learning do curso de pós-graduação Ciência de Dados e Analytics PUC Rio

---
## Análise de Previsão de Séries Temporais com Picos Esporádicos
Este projeto investiga a previsão de valores em séries temporais com ocorrência de picos esporádicos, utilizando técnicas de machine learning. O objetivo foi desenvolver um MVP (Minimum Viable Product) para antecipar eventos raros em um cenário de dados desbalanceados, servindo como baseline para evoluções futuras.

## Estrutura do Projeto
O projeto foi estruturado em uma jornada de descoberta e modelagem:

- A Base de Dados: Foi utilizado um dataset contendo valores reais de uma série temporal, onde a maioria das observações é zero e poucos picos positivos ocorrem em momentos específicos. Essa distribuição extremamente desbalanceada representou o maior desafio do projeto.

- O Baseline: A primeira abordagem foi estabelecer um modelo simples como referência inicial, priorizando a entrega de um protótipo funcional que permitisse identificar gargalos e direcionar esforços para iterações futuras.

- Análise de Resíduos: Os erros do modelo foram analisados detalhadamente para entender padrões de falha. Foi identificado que o modelo sofre de underfitting severo, com resíduos praticamente idênticos aos valores reais — indicando que o modelo não aprendeu nenhum padrão relevante.

- A Comparação: O desempenho do baseline foi confrontado com um modelo ideal (referência teórica), revelando lacunas significativas em capacidade preditiva, detecção de eventos e utilidade prática.

- Boas Práticas e Rastreabilidade: Todas as decisões, limitações e tentativas descartadas foram documentadas para garantir transparência e reprodutibilidade do projeto.

---

## Principais Conclusões
- O Modelo Falhou: O baseline atual prevê zero na maioria das observações, enquanto os dados reais apresentam picos positivos. Isso significa que nenhum evento importante é detectado — o modelo, da forma como está, não deve ser utilizado para esta previsão.

- Desbalanceamento é o Maior Inimigo: A classe majoritária (zeros) domina o conjunto de treino, fazendo com que o modelo aprenda a "vencer" prevendo sempre o valor mais frequente. Esse é o maior gargalo do projeto.

- Métricas Enganosas: MAE e MSE mascaram o verdadeiro desempenho em problemas com eventos raros. Métricas como Recall e F1-Score seriam mais adequadas para avaliar a detecção de picos.

- Features Temporais são Essenciais: A ausência de defasagens (lags), médias móveis e tendências foi uma das principais causas do fracasso do modelo. A engenharia de features é tão importante quanto a escolha do algoritmo.

- O Projeto Cumpriu seu Papel: Embora o resultado final seja negativo, o MVP cumpriu sua função mais importante: revelar com clareza o que não funciona e fornecer um roteiro claro para a próxima tentativa.
---
## Recomendações para Próximas Iterações
| Prioridade | Recomendação |
|------------|--------------|
| 🔴 Alta | Balanceamento de classes (SMOTE/oversampling) |
| 🔴 Alta | Criação de features temporais (lags, médias móveis) |
| 🔴 Alta | Mudança de métrica para Recall/F1-Score |
| 🟡 Média | Ponderação por amostra (pesos maiores para picos) |
| 🟡 Média | Modelo em dois estágios (detecção + regressão) |
| 🟢 Baixa | Trocar para algoritmos mais robustos (Random Forest/XGBoost) |
---
## Tecnologias Utilizadas
Python: Linguagem principal.

Pandas: Manipulação e tratamento de dados.

NumPy: Operações matemáticas.

Scikit-learn: Modelagem e métricas de avaliação.

Matplotlib & Seaborn: Visualizações e análise de resíduos.

Status do Projeto
🚨 MVP Concluído — Modelo não recomendado para produção.

O projeto entrega um diagnóstico preciso das falhas e um roteiro claro para evolução, mas não uma solução pronta para uso. Recomenda-se implementar as correções sugeridas antes de qualquer tentativa de deploy.
