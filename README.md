# FineTuning_TinyLlama

📋 Resumo do Projeto
Fine-tuning do modelo TinyLlama-1.1B-Chat-v1.0 usando dataset de perguntas e respostas médicas (16.407 exemplos).
✅ Etapas Concluídas
1. Preparação dos Dados

 Carregar dataset médico (train.csv - 16.407 linhas)
 Converter CSV para JSONL
 Criar template de prompt com formato Question/Answer
 Validar estrutura dos dados

2. Configuração do Ambiente

 Configurar device (GPU/CPU)
 Carregar modelo base: TinyLlama/TinyLlama-1.1B-Chat-v1.0
 Configurar tokenizer (pad_token = eos_token)
 Limpar cache CUDA

3. Tokenização

 Implementar função de tokenização
 Concatenar question + answer para modelo causal
 Aplicar padding e truncation (max_length: 2048)
 Criar labels = input_ids
 Split train/test (80/20)

4. Treinamento

 Configurar TrainingArguments

Learning rate: 1e-5
Max steps: 3
Batch size: 4
Gradient accumulation: 4
Optimizer: Adafactor


 Treinar modelo
 Salvar modelo fine-tunado

5. Avaliação

 Testar modelo base vs fine-tunado
 Implementar função de inferência
 Avaliar exact match em 10 exemplos
 Gerar tabela de predições vs targets

🔄 Melhorias Necessárias
Treinamento

 Aumentar max_steps para > 1000 (atualmente apenas 3)
 Testar diferentes learning rates
 Implementar early stopping adequado
 Adicionar mais épocas de treinamento
 Experimentar batch sizes maiores

Avaliação

 Implementar métricas além de exact match (BLEU, ROUGE)
 Expandir conjunto de teste (atualmente 10 exemplos)
 Adicionar validação cruzada
 Calcular métricas de similaridade semântica
 Avaliar qualidade médica das respostas

Dados

 Aumentar dataset (apenas 16k exemplos)
 Fazer data augmentation
 Balancear categorias de perguntas (qtype)
 Validar qualidade das respostas médicas

Código

 Remover código comentado desnecessário
 Melhorar logging e monitoring
 Adicionar checkpoints intermediários
 Implementar tratamento de erros robusto
 Documentar funções principais

Produção

 Testar em dados out-of-distribution
 Implementar API para inferência
 Otimizar para latência
 Adicionar testes unitários
 Criar pipeline de CI/CD

📊 Resultados Atuais

Exact Matches: 0/10 (modelo precisa de mais treinamento)
Steps treinados: 3 (muito baixo)
Dataset: 13.125 train / 3.282 test

🎯 Próximos Passos Imediatos

Re-treinar com min. 1000 steps
Avaliar em conjunto maior (100+ exemplos)
Implementar ROUGE score
Analisar exemplos onde modelo falha
Ajustar hyperparâmetros baseado em métricas
