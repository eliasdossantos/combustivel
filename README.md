# ⛽ Combustível

## Acesse o sistema:

- **https://combustivel-psi.vercel.app/**

Calculadora web para descobrir **qual combustível compensa mais na hora de abastecer**: gasolina comum, gasolina aditivada, etanol ou diesel. A decisão considera o preço por litro e o **consumo real** do carro ou da moto.

Feita com **HTML5, CSS3 e JavaScript puro**, em um único arquivo, sem frameworks, bibliotecas ou etapa de build.

## Funcionalidades

- **Dois modos de veículo**
  - **Gasolina / Etanol:** gasolina comum, gasolina aditivada (opcional) e etanol.
  - **Diesel:** diesel comum e diesel aditivado (opcional).
- **Cálculo automático:** os resultados atualizam a cada alteração, sem botão de calcular e sem recarregar a página.
- **Máscaras de entrada no padrão brasileiro**
  - Preços e valor do abastecimento: `R$ 6,20`, com vírgula nos centavos e ponto nos milhares.
  - Consumo: digitar `25` mostra `25 km/l`; aceita decimais (`12,5 km/l`).
- **Comparação por custo por km** usando o consumo real informado, com a economia a cada 100 km e a diferença percentual entre os combustíveis.
- **Regra dos 70%** (gasolina x etanol) como referência aproximada quando o consumo não é informado.
- **Simulação de abastecimento:** informando quanto quer gastar, mostra os litros e a autonomia estimada de cada combustível e qual rende mais.
- **Composição da gasolina:** percentual de etanol anidro editável (padrão 30%), com cálculo informativo do volume de etanol anidro e de gasolina A.
- **Tema claro e escuro:** segue o tema do sistema e permite alternar manualmente, guardando a escolha no navegador.
- **Layout responsivo** para celular, tablet e computador.
- **Botão "Limpar tudo"** para reiniciar a simulação.

## Como usar

1. Escolha o tipo de combustível: **Gasolina / Etanol** ou **Diesel**.
2. Informe o **preço por litro** de pelo menos dois combustíveis.
3. (Opcional, recomendado) Informe o **consumo em km/l** de cada combustível.
4. (Opcional) Informe **quanto deseja gastar** no abastecimento para ver litros e autonomia.
5. Veja o combustível recomendado, destacado em verde com ícone de confirmação.

## Como os cálculos funcionam

| Cálculo                   | Fórmula                                                                         |
| ------------------------- | ------------------------------------------------------------------------------- |
| Custo por km              | `preço por litro ÷ consumo (km/l)`                                              |
| Custo a cada 100 km       | `custo por km × 100`                                                            |
| Economia a cada 100 km    | `(custo por km do mais caro − custo por km do mais barato) × 100`               |
| Diferença percentual      | `(custo do mais caro − custo do mais barato) ÷ custo do mais barato × 100`      |
| Regra dos 70%             | `preço do etanol ÷ preço da gasolina × 100` (etanol tende a compensar se ≤ 70%) |
| Litros no abastecimento   | `valor a gastar ÷ preço por litro`                                              |
| Autonomia estimada        | `litros × consumo (km/l)`                                                       |
| Etanol anidro na gasolina | `litros de gasolina × percentual de etanol ÷ 100`                               |
| Gasolina A                | `litros de gasolina − litros de etanol anidro`                                  |

### Qual resultado vale

- **Com consumo informado** em pelo menos dois combustíveis, a comparação é pelo **custo por km**, que sempre tem prioridade.
- Se a regra dos 70% e o consumo real divergirem, a página prioriza o consumo real, explica a diferença e mostra o ponto de equilíbrio do seu veículo.
- **Sem consumo**, a página usa a regra dos 70% (gasolina x etanol) ou o menor preço por litro (diesel), avisando que é uma estimativa.

### Transparência

- A gasolina vendida no Brasil contém etanol anidro. O percentual padrão é **30%**, editável entre 0% e 100% e com botão para restaurar o padrão.
- Esse percentual é **apenas informativo**: nenhum desconto ou acréscimo é aplicado automaticamente ao consumo da gasolina, pois a eficiência depende do veículo, da calibração do motor e das condições de condução.
- O mesmo vale para **gasolina aditivada** e **diesel aditivado**: nenhum ganho de consumo é presumido. Informe o consumo real que você obtém com cada um.
- O diesel só é comparável a outro diesel, pois só pode ser usado em veículos a diesel.

## Validação dos dados

- Não há cálculo com campos vazios ou valores negativos.
- Consumo igual a zero e percentual de etanol fora de 0%–100% geram mensagens claras de erro.
- Valores monetários são tratados em centavos (inteiros) para evitar erros de arredondamento.

## Tecnologias

- HTML5
- CSS3 (variáveis CSS, grid, flexbox, tema claro/escuro)
- JavaScript puro (ES6+), sem dependências
- Ícones em SVG embutido

## Executando o projeto

Não precisa instalar nada. Clone o repositório e abra o arquivo no navegador:

```bash
git clone https://github.com/<seu-usuario>/combustivel.git
cd combustivel
# abra index.html no navegador (ou renomeie para index.html)
```

## Personalização

- **Percentual padrão de etanol:** altere o `value="30"` do campo `#mix` e o texto do botão "Restaurar 30%".
- **Combustíveis:** a lista fica no array `FUELS`, no início do bloco de JavaScript. Cada item define chave, nome, ícone, modo (`flex` ou `diesel`) e se é opcional.
- **Cores e tema:** ficam nas variáveis CSS em `:root`, com a versão escura em `[data-theme="dark"]`.

## Estrutura

```
combustivel/
├── index.html   # HTML, CSS e JavaScript em um único arquivo
└── README.md
```

## Aviso

Os resultados são estimativas baseadas nos valores informados e não substituem a medição do consumo real do seu veículo.
