# Lnks
> Feature permite que o anfitrião acesse os principais formulários que ele precisa.
## Como está codado
- Cada botão é um link que leva pro seu respectivo form do google.
- Ao clicar no botão o form abre em uma nova guia.

```bash
const handleGoToLink = (path: string) => {
    window.open(path, '_blank');
  };
```
## Onde está o código
**Front-end:**

[Componente LinksPage](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/LinksPage)

[Page](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/pages/LinkPage)
## O que está hard coded?

