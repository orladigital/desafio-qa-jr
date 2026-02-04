# Instruções Detalhadas - Desafio Técnico QA Jr.

Este documento contém as instruções detalhadas para completar o desafio técnico.

---

## 📋 Visão Geral

O desafio é dividido em três partes:

1. **Perguntas Teóricas**
2. **Planejamento de Testes**
3. **Desafio Prático de Automação**

---

## Parte 1: Perguntas Teóricas

### Objetivo
Avaliar seu conhecimento teórico sobre QA, testes, boas práticas e conceitos fundamentais.

### Instruções

1. Abra o arquivo `perguntas/perguntas-teoricas.md`
2. Responda todas as perguntas diretamente no arquivo, preenchendo os espaços indicados
3. Use exemplos quando apropriado
4. Não há resposta "certa" ou "errada" - queremos entender seu raciocínio

### Dicas
- Seja claro e objetivo
- Use exemplos práticos quando possível
- Demonstre seu conhecimento, mas não precisa ser extenso
- Se não souber algo, seja honesto e explique o que você faria para descobrir

---

## Parte 2: Planejamento de Testes

### Objetivo
Avaliar suas habilidades de planejamento, análise de requisitos e documentação de cenários de teste.

### Instruções

1. Leia atentamente a descrição da feature em `planejamento-teste/feature-ficticia.md`
2. Analise todos os requisitos funcionais e regras de negócio
3. Crie um arquivo MD na pasta `planejamento-teste/` (ex: `cenarios-teste.md` ou `meus-cenarios.md`) para documentar os cenários de teste
4. Organize os cenários de forma clara e estruturada

---

## Parte 3: Desafio Prático de Automação

### Objetivo
Avaliar suas habilidades práticas de automação, organização de código e resolução de problemas.

### Aplicação para Testar

Você pode escolher **uma** das seguintes opções:

#### Opção 1: Site Público (Recomendado)
Use o site **[The Internet](https://the-internet.herokuapp.com/)** para criar seus testes.

#### Opção 2: Outro Site Público
Se preferir, você pode usar outro site público conhecido (ex: Google, GitHub, etc.) e criar testes para funcionalidades específicas. **Importante**: Documente qual site você escolheu e por quê.

### Requisitos Obrigatórios

1. **Criar pelo menos 3 testes** cobrindo os cenários principais
2. **Criar README** explicando como executar os testes
3. **Documentar** os testes criados

### Requisitos Desejáveis (Bônus)

- Adicionar mais testes além do mínimo obrigatório
- Documentar decisões técnicas importantes
- Tratar casos de erro e edge cases
- Usar fixtures ou dados de teste

### Estrutura Esperada

```
desafio-pratico/
├── README.md                    # Como executar os testes
├── package.json                 # Dependências
├── cypress/ ou playwright/      # Estrutura da ferramenta escolhida
│   ├── e2e/                    # Testes E2E
│   ├── fixtures/               # Dados de teste (opcional)
│   └── support/                # Comandos customizados (opcional)
└── [outros arquivos de configuração]
```

---

## 📤 Como Entregar

### Fork e Pull Request (Recomendado)

1. Faça fork deste repositório
2. Trabalhe na branch `candidato-[seu-nome]`
   ```bash
   git checkout -b candidato-joao-silva
   ```
3. Complete o desafio na sua branch
4. Faça commit e push **apenas da sua branch**:
   ```bash
   git add .
   git commit -m "feat: completa desafio técnico"
   git push origin candidato-joao-silva
   ```
5. Abra um Pull Request da sua branch para a branch `main`

> ⚠️ **Importante**: 
> - A branch `main` está protegida e você **não conseguirá** fazer push direto nela
> - Trabalhe sempre na sua branch pessoal
> - Se tentar fazer push na `main`, receberá um erro de permissão

---

**Boa sorte!** 🍀
