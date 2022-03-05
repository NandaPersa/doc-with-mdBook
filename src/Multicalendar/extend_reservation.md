# Estender reserva
> Feature permite que o usuário estenda reservas tanto para check-in como para check-out
## Como está codado?
- Ao clicar na reserva/bloqueio o modal lateral abre com todos os Dados da reserva/bloqueio.
- Na parte inferior do modal tem o botão `Estender a reserva`.
- Ao clicar no botão de estender reserva, o sistema abre um novo modal com 3 opções de extensão para o usuário:
    - **`Early check-in:`** faz uma extensão do tipo check-in de apenas um dia.
    - **`Late check-out:`** faz uma extensão do tipo check-out, de apenas um dia. 
    - **`Extensão:`** o usuário escolhe entre uma extensão do tipo check-in ou check-out, sendo que nesta opção há a possibilidade de estender mais de um dia.
- Ao escolher Early check-in ou Late check-out o sistema mostra os campos de valor, forma de pagamento e notas para serem preenchidos.
- Ao escolher a opção Extensão o usuário escolhe se será extensão de check-in ou check-out e depois seleciona uma nova data para esse evento.
    - O cálculo do preço é baseado no número de dias estendidos.
    - Ao selecionar `Sim` em `Gerar um novo contrato` o sistema mostra uma série de campos para serem preenchidos e o novo contrato deverá ser gerado.
- Ao clicar no botão de estender reserva, o sistema faz um POST no endpoint `calendar/reservations/`.
Os seguintes campos deverão assumir os valores abaixo na reserva estendida:
    - early ou check-in
        ```bash
        is_early_extension: true,
        original_reservation: apontará para o id da reserva original
        ```
    - late ou check-out
        ```bash
        is_late_extension: true,
        original_reservation: apontará para o id da reserva original
        ```
- Após isso, a api com a endpoint em `calendar/reservations/` deverá ser chamada novamente, dessa vez com o método PUT para atualizar na reserva original os campos abaixo:
    - early ou check-in
        ```bash
        has_early_extension: true,
        early_extension_reservation: aponta para o id da extensão de early
        ```
    - late ou check-out
        ```bash
        has_late_extension: true,
        late_extension_reservation: aponta para o id da extensão de late
        ```

- A extensão criada deverá aparecer no calendário na cor verde claro assim que a reserva for estendida.
- ao clicar novamente na reserva, caso já exista uma extensão de check-in: novas extensões de check-in serão bloqueadas. A mesma ideia é válida para as extensões de check-out.
- Ao ser realizada uma extensão de check-in e uma extensão de check-out, o botão de estender reservas ficará desabilitado, e o texto mudará para “reserva já estendida".
- o usuário não deve ser capaz de estender uma reserva sobre outra reserva ativa.
- o usuário não deve ser capaz de estender o checkout de uma reserva que já possui uma extensão de checkout.
- o usuário não deve ser capaz de estender o check in de uma reserva que já possui uma extensão de check in.

- O modal fecha automaticamente ao final da requisição de estender a reserva.
## Onde está o código?

[Modal estender reserva](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/Calendar/Reservation/ModalExtendReserve)

## O que está hard coded?
A lógica precisa ser diferente para cada uma das 3 opções 
A parte mais complexa do componente está em atualizar o estado do dataGrouped, o que pede uma refatoração futura.
