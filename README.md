# Desenvolvimento de um Sistema Híbrido de Detecção de Fraude 🛡️🤖

Este repositório contém os códigos, metodologias e resultados do desenvolvimento de um ecossistema inteligente de prevenção à fraude em transações com cartões de crédito. O projeto combina a capacidade preditiva de algoritmos de Machine Learning (**Random Forest**) com o determinismo de **Heurísticas de Negócio** e a conformidade ética exigida pela LGPD/GDPR através da **anonimização de dados**.

---

## 🚀 Visão Geral do Projeto

O grande desafio de sistemas antifraude tradicionais reside no desbalanceamento severo de classes e na sofisticação dos ataques contemporâneos (*Carding*, Invasão de Contas, Ataques de Força Bruta). 

Este projeto propõe uma abordagem em camadas (Defesa em Profundidade):
1. **Camada Heurística:** Filtros baseados em regras de negócio críticas (ex: velocidade de transação, falhas sucessivas de autenticação) que geram um score de risco preliminar.
2. **Camada de Inteligência Artificial:** Um modelo supervisionado treinado para aprender comportamentos complexos e camuflagens que escapam de regras fixas.
3. **Privacidade de Dados:** Mascaramento e criptografia por *hash* de dados sensíveis na camada de engenharia de atributos.

---

## 📊 Metodologia Experimental (Os 15 Testes de Estresse)

O motor híbrido foi submetido a uma esteira rigorosa de **15 cenários experimentais** para testar seus limites de resiliência. Os dados foram extraídos e validados utilizando o ambiente Kaggle. Os experimentos englobaram desde o cenário base ideal até o "Caos Absoluto" (injeção de ruídos, remoção de colunas essenciais e inserção de clientes com perfis atípicos/VIPs).

### Evolução da Performance

Para abrir o capítulo de resultados, o gráfico abaixo consolida o comportamento das métricas conforme elevamos a complexidade do ambiente de teste:

![Evolução das Métricas sob Estresse](CAMINHO_DA_SUA_IMAGEM/evolucao_metricas_artigo.png)

*Insight:* Enquanto a Acurácia Geral manteve-se estável, o **Recall (Métrica de Ouro)** oscilou de forma controlada nos cenários de maior estresse, demonstrando que o sistema não entra em colapso sob dados corrompidos ou ataques coordenados.

---

## 🧪 O Desafio do Balanceamento: SMOTE vs. ADASYN

Um dos focos principais desta pesquisa foi o tratamento estatístico do desequilíbrio de classes. Avaliamos as duas técnicas mais populares de sobreamostragem sintética (*Oversampling*):

### 1. SMOTE (Teste 14º)
Ao equilibrar a base em 50/50 de forma uniforme, a fronteira de decisão acabou gerando um "ruído de vizinhança", fazendo com que o modelo sofresse sua maior degradação de sensibilidade, fechando com um **Recall de 0.95**.

### 2. ADASYN (Teste 15º)
Diferente do método anterior, o ADASYN focou a criação de dados sintéticos especificamente nas zonas de transição mais difíceis (onde fraudes tentavam mimetizar transações de clientes VIP). O resultado foi a recuperação total da sensibilidade, atingindo **1.0 (100%) de Recall**.

O impacto comparativo dessas técnicas e dos cenários de estresse pode ser visualizado no ranking abaixo:

![Ranking de Impacto no Recall](CAMINHO_DA_SUA_IMAGEM/impacto_estresse_comparativo.png)

---

## 🧩 Matrizes de Confusão (Validação Kaggle)

As matrizes extraídas do ambiente Kaggle validam visualmente a distribuição dos acertos do modelo. O sistema híbrido garantiu o controle estrito sobre os **Falsos Positivos** (evitando o bloqueio de clientes legítimos como no "Paradoxo do VIP") ao mesmo tempo em que zerou os Falsos Negativos em ataques críticos automatizados.

*(Insira aqui as imagens das matrizes que você possui)*
| Cenário Base (Teste 1º) | Cenário de Caos (Teste 11º) |
| :---: | :---: |
| ![Matriz Ideal](CAMINHO_DA_SUA_IMAGEM/matriz_azul.png) | ![Matriz Caos](CAMINHO_DA_SUA_IMAGEM/matriz_roxa.png) |

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem Principal:** Python 3.x
* **Manipulação e Estatística:** `pandas`, `numpy`
* **Machine Learning & Amostragem:** `scikit-learn`, `imblearn` (SMOTE/ADASYN)
* **Visualização de Dados:** `matplotlib`, `seaborn`
* **Ambiente de Computação:** Kaggle Notebooks

---

## 📈 Conclusão

Os resultados demonstraram que a fusão de heurísticas de negócio com inteligência algorítmica adaptativa cria um sistema altamente resiliente. O uso do **ADASYN** provou ser a abordagem superior para o tratamento de fraudes financeiras complexas, permitindo manter os sistemas seguros mesmo sob condições adversas e em estrita conformidade com a LGPD.
