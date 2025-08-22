Esse projeto foi desenvolvido através de colaboração do Núcleo Macro da Liga de Mercado Financeiro da FGV-Rio com a Mar Asset Management.

# Índice de Posição Política (IPP)

Este projeto tem como objetivo construir um **Índice de Posição Política (IPP)** para a Argentina, que sintetiza a distribuição ideológica dos votos no país em diferentes eleições.  
O IPP é uma métrica contínua em um **espectro de -2 a +2**, onde:

- **-2** → Extrema esquerda  
- **-1** → Esquerda / centro-esquerda  
- **0** → Centro político / peronismo moderado  
- **+1** → Centro-direita  
- **+2** → Direita radical / extrema direita  

---

##  Metodologia

1. **Fonte de Dados**  
   - Resultados eleitorais oficiais da Argentina (Câmara de Deputados, Senado e Presidência).  
   - Base em formato CSV com os votos por agrupação política.  

2. **Tratamento dos Dados**  
   - Padronização dos nomes das frentes/partidos:  
     - Remoção de acentos e caracteres especiais.  
     - Unificação de variações de nomes (ex.: `"JUNTOS POR EL CAMBIO - MENDOZA"` → `"JUNTOS POR EL CAMBIO"`).  
   - Exemplo de normalização implementada:  
     - `"JUNTOS POR EL CAMBIO..."` → **JUNTOS POR EL CAMBIO**  
     - `"HACEMOS..."` → **HACEMOS**  
     - `"FRENTE DE IZQUIERDA Y DE TRABAJADORES..."` → **FRENTE DE IZQUIERDA Y DE TRABAJADORES**  
     - `"FRENTE DE TODOS"` / `"UNIÓN POR LA PATRIA"` → **UNIÓN POR LA PATRIA**

3. **Classificação Ideológica** 
   Exemplo:
   Cada frente eleitoral é mapeada no espectro [-2, 2]:  
   | Frente / Partido                              | Posição |
   |-----------------------------------------------|---------|
   | Frente de Izquierda y de los Trabajadores     | -2      |
   | Frente de Todos / Unión por la Patria         | -1      |
   | Hacemos por Nuestro País                      | 0       |
   | Juntos por el Cambio                          | +1      |
   | La Libertad Avanza                            | +2      |

4. **Cálculo do IPP**  
   - Para cada eleição, calcula-se a **média ponderada** das posições ideológicas, usando como pesos a porcentagem de votos de cada frente.  
   - Fórmula simplificada:  

   $$
     IPP = \frac{\sum_{i}(votos_i \times posicao_i)}{\sum_{i} votos_i}
   $$
---

## 📊 Objetivos do Projeto

- Criar uma métrica simples e comparável da posição ideológica média do eleitorado argentino.  
- Permitir análise.
- Oferecer base para comparações internacionais, aplicando a mesma metodologia em outros países.  

---

## Como utilizar

- Extraia os arquivos de dentro da pasta \datasets_eleicoes_argentina.zip, contido na última Release, para a pasta \data.
- Rode o Jupyter Notebook

## 🚀 Próximos Passos

- Incluir **dados históricos anteriores a 2013**.  
- Estender a metodologia para **outros países latino-americanos**.  
- Visualizações gráficas da evolução do IPP ao longo do tempo.  

---