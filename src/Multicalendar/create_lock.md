# Criar novo bloqueio
> Essa feature permite que o usuário bloqueie um imóvel por um período de tempo impedindo que ele receba reservas durante o período selecionado.
## Como está codado?
- O formulário para criar bloqueio é o mesmo formulário de criar reserva.
- Todas as células de data do calendário são clicáveis, ao clicar em uma ou mais células o sistema abre um modal de opções.
- Ao clicar na opção “Criar bloqueio” o sistema abre um modal lateral para o usuário preencher as informções do bloqueio.
- O campo `Datas` e `Motivo do bloqueio` são obrigatórios. Além disso o sistema valida se a data de checkout é maior que a data de checkin. A validação desses campos é feita usando o Yup.

```bash
const validationBlock = Yup.object().shape({
    reason: Yup.string().required(),
    checkInDate: Yup.date().required(),
    checkOutDate: Yup
      .date()
      .when('checkInDate',
        (checkInDate: any, schema: Yup.DateSchema) => (
          checkInDate && schema.min(checkInDate, 'A data deve ser maior que data de check-in')))
      .required(),
  });
```
- Ao clicar no botão “Salvar” o sistema faz um post no endpoint `/calendar/blocking/`:
```bash
export const postBlocking = async (values: BlockFormData) => {
  await Promise.all(values.properties.map((property) => (
    request.post('/calendar/blocking/', {
      code: uuid(),
      check_in_date: moment(values.checkInDate).format('DD/MM/YYYY'),
      check_out_date: moment(values.checkOutDate).format('DD/MM/YYYY'),
      blocking_reason: values.blockingReason.value,
      comment: values.notes,
      property: property.id,
      status: 'Active',
    }))));
};
```
## Onde está o código?
**Frontend** 

[Interface do componente](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/Calendar/Reservation/Modal)

[Requisições a APIs](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Reservation)
## O que está hard coded?
- O formulário para criar bloqueio é o mesmo de criar reserva, usamos uma variável chamada `isReservation` que recebe `true` ou `false`, quando o valor for `false` apenas os campos usados no bloqueio são mostrados. 
- O simple select `Motivo do bloqueio` está estático no front, não é carregado pela API. O envio desses campos está sendo feito enviando o nome em inglês do motivo para o endpoint de criação de bloqueio `/calendar/blocking/`.
