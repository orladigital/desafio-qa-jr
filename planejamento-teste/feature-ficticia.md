# Feature Fictícia: Sistema de Reserva de Salas de Reunião

## 📋 Descrição da Feature

A empresa está desenvolvendo um sistema interno para gerenciar reservas de salas de reunião. Esta feature permite que funcionários visualizem salas disponíveis, façam reservas e gerenciem suas reservas existentes.

---

## 🎯 Objetivo

Criar um sistema que permita aos funcionários:
- Visualizar salas de reunião disponíveis
- Fazer reservas de salas
- Visualizar e gerenciar suas próprias reservas
- Cancelar reservas (com algumas restrições)

---

## 📝 Requisitos Funcionais

### RF01 - Visualização de Salas Disponíveis

**Descrição**: O sistema deve exibir uma lista de todas as salas de reunião com suas informações básicas.

**Informações a exibir**:
- Nome da sala (ex: "Sala A", "Sala B", "Sala de Conferência")
- Capacidade (número máximo de pessoas)
- Localização (andar e número)
- Recursos disponíveis (projetor, TV, quadro branco, videoconferência)
- Status atual (Disponível, Ocupada, Em Manutenção)

**Regras de Negócio**:
- Salas em manutenção não devem aparecer na lista de disponíveis
- A lista deve ser ordenada por nome da sala (ordem alfabética)

---

### RF02 - Busca e Filtros

**Descrição**: O usuário deve poder buscar e filtrar salas por diferentes critérios.

**Filtros disponíveis**:
- Por capacidade mínima (ex: mostrar apenas salas que cabem pelo menos 5 pessoas)
- Por recursos (projetor, TV, quadro branco, videoconferência)
- Por localização (andar)
- Por disponibilidade (disponível agora, disponível em uma data/hora específica)

**Busca**:
- Busca por nome da sala (busca parcial, case-insensitive)

**Regras de Negócio**:
- Múltiplos filtros podem ser aplicados simultaneamente
- Ao limpar filtros, a lista deve retornar ao estado inicial

---

### RF03 - Fazer Reserva

**Descrição**: O usuário deve poder fazer uma reserva de uma sala disponível.

**Campos do formulário de reserva**:
- **Sala** (obrigatório): Seleção da sala (dropdown com salas disponíveis)
- **Data** (obrigatório): Data da reserva (formato DD/MM/YYYY)
- **Hora de início** (obrigatório): Hora de início (formato HH:MM, intervalo de 30 em 30 minutos)
- **Hora de fim** (obrigatório): Hora de término (formato HH:MM, intervalo de 30 em 30 minutos)
- **Título da reunião** (obrigatório): Nome/descrição da reunião (mínimo 5 caracteres, máximo 100 caracteres)
- **Número de participantes** (obrigatório): Número de pessoas (mínimo 1, máximo igual à capacidade da sala)
- **Observações** (opcional): Notas adicionais (máximo 500 caracteres)

**Validações**:
- Data não pode ser no passado
- Data não pode ser mais de 30 dias no futuro
- Hora de fim deve ser posterior à hora de início
- Duração mínima: 30 minutos
- Duração máxima: 8 horas
- Número de participantes não pode exceder a capacidade da sala
- Não pode haver conflito com outra reserva na mesma sala, data e horário

**Regras de Negócio**:
- Reservas só podem ser feitas em horário comercial (08:00 às 18:00)
- Um usuário pode ter no máximo 3 reservas ativas simultaneamente
- Após criar a reserva, o usuário recebe um e-mail de confirmação
- A reserva é criada com status "Confirmada"

---

### RF04 - Visualizar Minhas Reservas

**Descrição**: O usuário deve poder visualizar todas as suas reservas.

**Informações exibidas**:
- Nome da sala
- Data e horário (início e fim)
- Título da reunião
- Número de participantes
- Status (Confirmada, Cancelada, Concluída)
- Botões de ação (Ver detalhes, Cancelar)

**Filtros e ordenação**:
- Filtrar por status (Todas, Confirmadas, Canceladas, Concluídas)
- Filtrar por período (Hoje, Esta semana, Este mês, Todas)
- Ordenar por data (mais recente primeiro ou mais antiga primeiro)

**Regras de Negócio**:
- Reservas concluídas aparecem em uma seção separada
- Reservas canceladas aparecem com visual diferenciado

---

### RF05 - Cancelar Reserva

**Descrição**: O usuário deve poder cancelar suas próprias reservas.

**Regras de Negócio**:
- Apenas o criador da reserva pode cancelá-la
- Reservas que já começaram não podem ser canceladas
- Reservas podem ser canceladas até 2 horas antes do horário de início
- Ao cancelar, o usuário deve confirmar a ação em um modal de confirmação
- Após cancelamento, a sala fica disponível para outras reservas
- O usuário recebe um e-mail de confirmação do cancelamento

**Exceções**:
- Reservas de mais de 4 horas podem ser canceladas até 24 horas antes
- Administradores podem cancelar qualquer reserva a qualquer momento

---

### RF06 - Detalhes da Reserva

**Descrição**: Ao clicar em uma reserva, o usuário deve ver os detalhes completos.

**Informações exibidas**:
- Todas as informações da reserva (sala, data, horário, título, participantes, observações)
- Status atual
- Data de criação da reserva
- Histórico de alterações (se houver)
- Botões de ação disponíveis (Cancelar, se aplicável)

---

## 🔒 Regras de Segurança e Permissões

- Apenas usuários autenticados podem acessar o sistema
- Usuários só podem ver e gerenciar suas próprias reservas
- Administradores têm acesso a todas as reservas e podem cancelar qualquer reserva
- Todas as ações devem ser registradas em log de auditoria

---

## 📱 Interface

- **Responsivo**: O sistema deve funcionar em desktop, tablet e mobile
- **Acessibilidade**: Deve seguir padrões WCAG 2.1 nível AA
- **Idioma**: Português (Brasil)

---

## ⚠️ Casos Especiais

1. **Conflito de reserva**: Se dois usuários tentarem reservar a mesma sala no mesmo horário simultaneamente, apenas o primeiro a confirmar deve ter sucesso
2. **Manutenção**: Administradores podem marcar salas como "Em Manutenção", o que impede novas reservas
3. **Fuso horário**: O sistema usa horário de Brasília (UTC-3)
4. **Feriados**: O sistema deve considerar feriados nacionais e não permitir reservas nesses dias (configurável por administrador)

---

## 🎨 Mockups e Referências

*Nota: Para este desafio, você não precisa criar mockups. Use sua imaginação e conhecimento de padrões de UI/UX para planejar os testes.*

---

## 📊 Dados de Exemplo

**Salas disponíveis**:
- Sala A: Capacidade 4, 2º andar, Projetor + TV
- Sala B: Capacidade 8, 2º andar, Projetor + Quadro Branco
- Sala de Conferência: Capacidade 20, 1º andar, Projetor + TV + Videoconferência
- Sala Pequena: Capacidade 2, 3º andar, Quadro Branco

**Usuário de teste**:
- Nome: João Silva
- Email: joao.silva@empresa.com
- Perfil: Funcionário comum (não administrador)

---

## ✅ Critérios de Aceitação (Resumo)

1. ✅ Usuário pode visualizar lista de salas disponíveis
2. ✅ Usuário pode filtrar e buscar salas
3. ✅ Usuário pode fazer uma reserva válida
4. ✅ Sistema valida todos os campos e regras de negócio
5. ✅ Usuário pode visualizar suas reservas
6. ✅ Usuário pode cancelar reservas dentro das regras estabelecidas
7. ✅ Sistema impede conflitos de reserva
8. ✅ Sistema envia e-mails de confirmação

---

**Agora é com você!** Use esta descrição para planejar e documentar os cenários de teste desta feature.
