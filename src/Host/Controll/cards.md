# Cards checkin/checkout/limpeza
> Feature que permite o usuário ver mais informações dos eventos de checkin, checkout e limpeza por meio de cards e realizar ações.

- Os cards de checkout e checkin contém as principais informações da reserva e botões de ação.
- Os cards de limpeza possuem apenas o código do imóvel, endereços e botões de ação.
- As informações endereço, telefone e código da reserva possuem um botão ao lado que copia esses respectivos dados para área de tranferência.
- O campo copiar reserva copia todas as informações da reserva.
- O card de checkin de reserva possui as seguintes ações:
    - 1. Enviar mensagem inicial.
    - 2. Preencher informações.
    - 3. Realizar check-in.
    - 4. Concluir check-in
- O card de checkin de bloqueio possui as seguintes ações:
    - 1. Preencher informações.
    - 2. Realizar check-in.
    - 3. Concluir check-in
- O card de checkin de checkout possui as seguintes ações:
    - 1. Enviar mensagem inicial.
    - 2. Preencher informações.
    - 3. Realizar check-out.
    - 4. Enviar pesquisa de feedback.
    - 5. Concluir checklist.
    - Danos dos hóspedes.
- O card de checkout de bloqueio possui as seguintes ações:
    - 1. Preencher informações.
    - 2. Realizar checkout.
    - 3. Concluir checklist
- O card de limpeza possui as seguintes ações:
    - 1. Preencher informações.
    - 2. Realizar limpeza.
    - 3. Finalizar vistoria.

- Ao clicar no no botão `1. Enviar mensagem inicial` o sistema abre um link do whatsapp web para enviar mensagem para o hóspede. A mensagem muda de acordo com o evento:

    - **`Evento de checkin:`** *"Olá {nome do hóspede}, tudo bem? Sou a , e serei sua anfitriã {nome do anfitrião logado}. Você pode entrar em contato comigo para tirar dúvidas sobre a estada por aqui e, um dia antes da sua entrada, marcamos o horário de encontro e te passo as informações que você precisa sobre o endereço! Só para confirmar, para quantas pessoas é a estada? Boa semana e até logo."*

    - **`Evento de checkout:`** *Olá {nome do hóspede} Neto! Infelizmente amanhã já é o dia do seu checkout. Gostaria de saber que horas vocês pretendem sair do imóvel, lembrando que a saída é até às 11h.*

- Ao clicar no botão `Preencher informações` o sistema abre um modal lateral para ser preenchido pelo host, ao clicar em `Salvar` o sistema faz um PUT ou POST no endpoint `xxx`.
- Ao clicar no botão `Realizar check-in` de um evento checkin o sistema abre o form checklist checkin em uma nova aba com o campo imóvel preenchido.
- Ao clicar no botão `Realizar check-in` de um evento checkout o sistema abre o form checklist checkout em uma nova aba com o campo imóvel preenchido.
- Ao clicar no botão `Concluir checkin` para eventos de checkin ou `Concluir checlist` ou `Concluir checklist`para eventos de checkout `Finalizar vistoria`para eventos de limpeza o sistema marca o card como concluído.
- Quando as informações são preenchidas e o card é marcado como concluido o sistema move o card para a seção concluídos.
- Ao clicar no botão `Enviar pesquisa de feedback` o sistema abre em uma nova aba um link do whatsapp com a seguinte mensagem: 
    > Olá {nome do hóspede}, agradecemos muito pela sua companhia nestes últimos dias, tenha uma ótima viagem de retorno! Trabalhamos constantemente para melhorar nosso serviço e nossos imóveis, então se você puder nos deixar seu feedback te agradecemos muito, é rapidinho, não vai levar mais de 3 minutos. Link: https://docs.google.com/forms/d/e/1FAIpQLSdrlj9QUuXhUDy_dpl2EE8Bf7Mz1eopDp-AE3LBpJ54LFMRRQ/viewform?usp=pp_url&entry.1675664374=2022-01-31&entry.683665135={code do imóvel}

- Ao clicar no botão `Danos dos hóspedes`o sistema abre em uma nova aba o form do google de Danos do hóspede.
- Ao clicar no botão `Realizar limpeza`o sistema abre em uma nova aba o form do google de Vistoria limpeza.
- Ao clicar sobre o código da reserva ou no botão copiar o sistema copia o código para area de transferencia;
- Ao clicar sobre o número de telefone ou no botão copiar o sistema copia o número para a área de transferência;
- Ao passar o mouse sobre os botões de copiar e origem da reserva deve aparecer um texto indicando o que eles fazem;

## Onde está o código

[Modal](hfront/src/components/ControllerPage/Modal)


