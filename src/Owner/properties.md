# Imóveis
> Essa feature permite que o Proprietário visualize todos os seus imóveis
- Ao abrir a página de proprietário o sistema deve fazer um get no  endpoint `/properties/owner/` para mostrar todos os imóveis do proprietário logado, a página tem um limite de 4 imóveis sendo exibidos inicialmente, caso o proprietário tenha mais de 4 imóveis, uma opção “Mais propriedades” é mostrada para que o usuário consiga ver todas as propriedades;

- O sistema deve mostrar o status da propriedade, o status deve ser:
    - `Locado até DD/MM:` quando o imóvel estiver alugado e a cor da bolinha fica verde;
    - `Disponível:` quando o imóvel não possuir reserva em andamento, caso o imóvel tenha reservas futuras mostrar a data do próximo check-in, caso não tenha reservas futuras ffica vazio, a cor da bolinha fica azul;
    - `Bloqueado até DD/MM:` quando estiver com um bloqueio, a cor da bolinha fica vermelho;
    - `Inativo:` quando o contrato desse imóvel estiver cancelado, a cor da bolinha fica cinza.
- Os cards de propriedade devem ser ordenador de ativos para inativos. Os imóveis ativos devem ser ordenados por ordem de cadastramento no sistema;

- Os cards devem ser responsivo para mobile.

- Ao clicar em visualizar imóvel ou em qualquer parte do componente imóvel o sistema redireciona o usuário para a página de [Detalhes do imóvel](./property_details.md)

## Onde está o código?
**Front-end:**

[Componente imóvel](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/OwnerPage/CardProperties)

**Requisições a APIs:**

[Requisições](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/services/Owner/request.ts)

**Backend:**

[Apis](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/property/apis)

## O que está hard coded?