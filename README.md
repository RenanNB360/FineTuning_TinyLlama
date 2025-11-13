# FineTuning_TinyLlama

## 📋 Resumo do Projeto
Fine-tuning do modelo TinyLlama-1.1B-Chat-v1.0 usando dataset de perguntas e respostas médicas (16.407 exemplos).

## ✅ Etapas Concluídas

### 1. Preparação dos Dados
- [x] Carregar dataset médico (`train.csv` - 16.407 linhas)
- [x] Converter CSV para JSONL
- [x] Criar template de prompt com formato Question/Answer
- [x] Validar estrutura dos dados

### 2. Configuração do Ambiente
- [x] Configurar device (GPU/CPU)
- [x] Carregar modelo base: `TinyLlama/TinyLlama-1.1B-Chat-v1.0`
- [x] Configurar tokenizer (pad_token = eos_token)
- [x] Limpar cache CUDA

### 3. Tokenização
- [x] Implementar função de tokenização
- [x] Concatenar question + answer para modelo causal
- [x] Aplicar padding e truncation (max_length: 2048)
- [x] Criar labels = input_ids
- [x] Split train/test (80/20)

### 4. Treinamento
- [x] Configurar TrainingArguments
  - Learning rate: 1e-5
  - Max steps: 3
  - Batch size: 4
  - Gradient accumulation: 4
  - Optimizer: Adafactor
- [x] Treinar modelo
- [x] Salvar modelo fine-tunado

### 5. Avaliação
- [x] Testar modelo base vs fine-tunado
- [x] Implementar função de inferência
- [x] Avaliar exact match em 10 exemplos
- [x] Gerar tabela de predições vs targets

## 🔄 Melhorias Necessárias

### Treinamento
- [ ] Aumentar `max_steps` para > 1000 (atualmente apenas 3)
- [ ] Testar diferentes learning rates
- [ ] Implementar early stopping adequado
- [ ] Adicionar mais épocas de treinamento
- [ ] Experimentar batch sizes maiores

### Avaliação
- [ ] Implementar métricas além de exact match (BLEU, ROUGE)
- [ ] Expandir conjunto de teste (atualmente 10 exemplos)
- [ ] Adicionar validação cruzada
- [ ] Calcular métricas de similaridade semântica
- [ ] Avaliar qualidade médica das respostas

### Dados
- [ ] Aumentar dataset (apenas 16k exemplos)
- [ ] Fazer data augmentation
- [ ] Balancear categorias de perguntas (qtype)
- [ ] Validar qualidade das respostas médicas

### Código
- [ ] Remover código comentado desnecessário
- [ ] Melhorar logging e monitoring
- [ ] Adicionar checkpoints intermediários
- [ ] Implementar tratamento de erros robusto
- [ ] Documentar funções principais

### Produção
- [ ] Testar em dados out-of-distribution
- [ ] Implementar API para inferência
- [ ] Otimizar para latência
- [ ] Adicionar testes unitários
- [ ] Criar pipeline de CI/CD

## 📊 Resultados Atuais
- **Exact Matches**: 0/10 (modelo precisa de mais treinamento)
- **Steps treinados**: 3 (muito baixo)
- **Dataset**: 13.125 train / 3.282 test

## 🎯 Próximos Passos Imediatos
1. Re-treinar com min. 1000 steps
2. Avaliar em conjunto maior (100+ exemplos)
3. Implementar ROUGE score
4. Analisar exemplos onde modelo falha
5. Ajustar hyperparâmetros baseado em métricas
