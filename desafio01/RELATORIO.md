# Desafio 1: relatório

**Aluno(a):**

## 1. Versões dos dados

Rode o comando abaixo e complete a tabela com os 8 primeiros caracteres de cada md5:

```bash
for tag in dados-v1 dados-v2 dados-v3; do
  echo "$tag $(git show $tag:data/raw/bike.csv.dvc | awk '/md5/{print $3}')"
done
```

| Tag | md5 (8 primeiros caracteres) | Período |
|---|---|---|
| `dados-v1` | `fc7d423a` | 01/01/2011 a 31/12/2011 |
| `dados-v2` | `11e40c60` | 01/01/2011 a 30/06/2012 |
| `dados-v3` | `7747b2ef` | 01/01/2011 a 31/12/2012 |

## 2. Comparação no mesmo teste

Copie os números de `reports/comparacao.json`.

**Período do teste:** 2012-12-04 a 2012-12-31 (670 linhas)

| Alias | Versão | RMSE | MAE | R² |
|---|---|---|---|---|
| `@champion` | 5 | 94.42 | 67.08 | 0.65 |
| `@challenger` | 7 | 64.60 | 43.84 | 0.83 |

## 3. Decisão

**Promovido ou rejeitado?**
Promovido

**Justificativa (2 a 3 frases):**
O @challenger superou o @champion em todas as métricas

## 4. O que cada ferramenta fez nesse projeto?

**Pergunta 01:**
Com suas palavras, quais os dois usos do DVC nesse projeto?
Primeiro uso é o versionamento de dados fora do git
O segundo é declarar e reproduzir o pipeline em estágios

**Pergunta 02:**
Com suas palavras, para que serve o MLflow nesse projeto?
Serve para registrar e comparar as execuções de treino e para gerenciar as versões do modelo com o model registry. Por meio de aliases e tags de governança, permite tambem validar candidatos, promover ou fazer rollback de modelos sem alterar o consumidor

