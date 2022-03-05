# Multicalendar
![The Rust Logo](../../images/calendar.png)

O multicalendario é acessivel pelos usuários `Attendant`, `Host`, `Seazone` e `Admin`. Cada um desses usuários possuem diferentes permissões no calendário.
## Permissão Attendent 
O atendente tem acesso a todas as funcionalidades do calendário.
## Permissão Host 
O usuário Host tem acesso limitado ao calendário.
Ele pode:
- Criar bloqueios;
- Cancelar bloqueios;
- Visualizar reservas/bloqueio;
- Navegar entre as datas pelo mini calendário;
- Navegar entre as propriedades;
- Recolher categorias;
- Buscar um imóvel;
- Filtrar busca de imóvel.

Ele NÃO pode:
- Cancelar reserva;
- Criar reserva;
- Estender reserva;
- Ver dados financeiros da reserva.

As ações que ele não pode executar ficam ocultas.
## Permissão Seazone

## Permissão Admin

