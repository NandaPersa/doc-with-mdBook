# Cancelar reserva/bloqueio
> Feature que permite que o usuário cancele uma reserva
## Como está codado?
- Ao clicar na reserva/bloqueio o modal lateral abre com todos os Dados da reserva/bloqueio. 
- Na parte inferior existe um botão chamado `Cancelar reserva` (caso seja um bloqueio, o texto do botão deverá aparecer como cancelar bloqueio).
- Ao clicar no botão de `Cancelar reserva` o sistema abre um modal para inserir o motivo do cancelamento da reserva/bloqueio.
- Após preenchido o motivo do cancelamento e clicar no botão `Cancelar reserva`, o sistema chama a função `putReservationStatus` que faz um PUT no endpoint `calendar/reservations/` atualizando o campo status da reserva para *canceled*.
```bash
export const putReservationStatus = async (
  data: Reservation,
  newStatus: ReservationStatus,
  newComment: string,
  id: number,
) => {
  await request.put(`/calendar/reservations/${id}/`, {
    ...data,
    guest: data.guest.id,
    status: newStatus,
    comment: newComment,
  });
};
```
- Após cancelar a reserva a cor do marcador dela é alterada para cinza tanto no modal lateral quanto no calendário.
- Ao clicar sobre uma reserva já cancelada o botão de `Cancelar reserva` deve estar desabilitado.
- O sistema permite criar uma reserva no lugar de uma reserva cancelada.
## Onde está o código?
**frontend** 

[Modal cancelar reserva](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/Calendar/Reservation/ModalCancell)

**Requisições a APIs:** 

[Request reserva](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Reservation)

**Recursos de contextos (estados, funções, hooks):**

[Hook reservation](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/hooks/ReservationHook)

[Contexto reservation](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/context/ReservationContext.tsx)

**backend:**

[Api reservation](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/reservation)



## O que está hard coded?

