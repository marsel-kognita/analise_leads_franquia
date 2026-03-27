# Análise de Leads - Franquia

Projeto de análise descritiva de dados de estabelecimentos com foco em validação e classificação de telefones.

## 📋 Visão Geral

Este projeto realiza análises descritivas de uma base de dados de estabelecimentos, com ênfase especial em:

- **Validação de telefones**: identificação de números válidos segundo padrões brasileiros (10-11 dígitos com DDD válido)
- **Classificação de celulares**: distinção entre celulares e telefones fixos
- **Estatísticas descritivas**: análise de variáveis numéricas e categóricas
- **Detecção de valores ausentes**: identificação de lacunas e data quality

## 📁 Estrutura do Projeto

```
analise_leads_franquia/
├── README.md                              # Este arquivo
├── .gitignore                             # Configuração Git (exclui dados, cache, etc)
├── environment.yml                        # Especificação do ambiente Conda (reproduzível)
├── requirements.txt                       # Dependências Python principais
├── estabelecimentos_processado.csv        # Arquivo de dados brutos
├── dados/                                 # Pasta para dados processados/adicionais (excluída do Git)
└── notebooks/
    └── analise_descritiva_estabelecimentos.ipynb  # Análise principal em Jupyter Notebook
```

## 🚀 Configuração do Ambiente

### Opção 1: Usando Conda (Recomendado - Reproduzível)

Cria um ambiente Conda idêntico ao desenvolvido:

```bash
conda env create -f environment.yml
conda activate anaconda3
```

### Opção 2: Usando pip

Alternativa mais leve (usa Python do sistema):

```bash
pip install -r requirements.txt
```

## 📓 Como Executar o Notebook

1. **Abrir no VS Code/Jupyter:**
   ```bash
   jupyter notebook notebooks/analise_descritiva_estabelecimentos.ipynb
   ```

2. **Selecionar o kernel:**
   - Se usar Conda: selecione `Python (anaconda3)`
   - Se usar pip: selecione o kernel do Python padrão

3. **Executar as células** na ordem apresentada

## 📊 Análises Disponíveis

### 1. Informações Gerais
- Dimensões do dataset (linhas e colunas)
- Tipos de dados
- Valores ausentes

### 2. Estatísticas Descritivas
- Variáveis numéricas: média, mediana, desvio padrão, quartis
- Variáveis categóricas: contagem de valores únicos, frequência
- Cardinalidade das colunas

### 3. Validação de Telefones

#### Regras de Validação
- **Número válido**: 10-11 dígitos após limpeza, com DDD entre 11 e 99
- **Limpeza**: remoção de caracteres não-dígitos, zeros à esquerda (prefixo `00`/`0` de discagem interurbana), e código de país `55`

#### Classificação de Celular
- **11 dígitos**: DDD + 9 + 8 dígitos (formato atual, ex: `1199999999`)
- **10 dígitos**: DDD + 9XXXX-XXXX (formato antigo, ex: `1199999999`)

#### Resultados Esperados

| Campo | Preenchidos | Válidos | Celulares | % Válidos | % Celulares |
|-------|-------------|---------|-----------|-----------|-------------|
| telefone1 | 139.583 | 136.873 | 23.501 | 98.1% | 17.2% |
| telefone2 | 39.457 | 31.551 | 7.094 | 80.0% | 22.5% |

**Interpretação**: Base contém telefones de estabelecimentos (maioria fixos), com ~17-22% sendo celulares.

## 📦 Dependências Principais

- **pandas**: manipulação e análise de dados
- **numpy**: operações numéricas
- **matplotlib**: visualizações estáticas
- **seaborn**: visualizações estatísticas
- **jupyter/jupyterlab**: ambiente de notebook interativo
- **scikit-learn**: ferramentas de machine learning (preparação para análises futuras)

## 🔧 Ferramentas de Desenvolvimento

- **Python**: 3.12
- **Conda**: gerenciador de ambientes
- **Jupyter**: notebook interativo
- **Git**: controle de versão

## 📝 Notas sobre os Dados

- O arquivo principal `estabelecimentos_processado.csv` contém dados de estabelecimentos
- A pasta `dados/` é para dados adicionais/processados e está excluída do Git (`.gitignore`)
- A validação de telefones detecta automaticamente diferentes formatos e características regionais

## 🔮 Próximos Passos Sugeridos

- Enriquecer análises com visualizações gráficas
- Criar análise de padrões geográficos (por DDD)
- Implementar detecção de anomalias em telefones
- Adicionar análises de correlação entre variáveis
- Exportar resultados em formatos estruturados (Parquet, SQL)

## ✅ Checklist de Configuração

- [ ] Environment criado e ativado
- [ ] Kernel Jupyter selecionado
- [ ] Notebook executado sem erros
- [ ] Análises descritivas visíveis
- [ ] Validações de telefone rodando

## 📧 Contato

Para dúvidas ou sugestões sobre este projeto, consulte o repositório.

---

**Última atualização**: Março 2026  
**Versão do projeto**: 1.0
