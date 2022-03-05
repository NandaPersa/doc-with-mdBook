# Controle
> Essa feature permite ao usuário visualizar eventos de checkin, checkout e limpeza por semana, preencher informações desses eventos e alternar entre as semanas de acordo com sua vontade. 
## Como está codado
- Ao abrir a página de Controle o sistema deve fazer 3 GET’s  no endpoint `/host_controller/` um para mostrar os checkins, um para mostrar os checkouts e um para mostrar as limpezas.
- O sistema deve fazer um filtro por data em todos os checkins, checkouts e limpeza, os check-ins são ordenados de acordo com a data de check-in da reserva e os checkouts de acordo com a data de check-out.
- Quando clicado na opção de `Próxima semana` o calendário é atualizado para os próximos 7 dias contando a partir do último que estáva sendo mostrado.
- Quando clicado na opção `Semana anterior`, o calendário semanal mostrado deve ser atualizado para os 7 dias anteriores contando a partir do dia atual.
- Além do calendário os cards também devem ser atualizados de acordo com a semana selecionada.
- Os cards podem ser filtrados por tipo de evento(checkin, checkout e limpeza) através do checkbox, se todos os checkboxes estiverem selecionados o sistema mostra todos os eventos, se apenas um checkbox for selecionado o sistema deve mostrar apenas as eventos relacionados a ele, se mais de um checkbox for selecionado o sistema deve mostrar as tarefas relacionadas aos checkboxes selecionados.
- Ao clicar sobre um card o sistema deve abrir um modal ao lado do card selecionado com mais [informações sobre a tarefa](./cards.md).
- A página de controle do anfitrião deve ser responsivo para mobile.

  
## Onde está o código

[Página controle](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/pages/Controller)

[Componente controle](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/ControllerPage)

[Componente Header](front/src/components/ControllerPage/HeaderContainer/HeaderConfig.tsx)

**Recursos de contextos (estados, funções, hooks):**
[Contexto controllerPage](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/context/ControllerPage)


## O que está hard coded?
- O endpoint usado para mostrar os dados de checkin, checkout  e limpeza é o mesmo, mudando apenas os parâmetros que são enviados. Para checkin os seguintes parâmetros são enviados: check_in_initial_date e check_in_final_date.
- Para checkout são enviados os seguintes parâmetros: check_out_initial_date e check_out_final_date.
- Para limpeza os seguintes parâmetros são enviados: check_out_initial_date e check_out_final_date.
