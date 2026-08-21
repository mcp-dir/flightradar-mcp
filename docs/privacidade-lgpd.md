# Privacidade & LGPD

Flight Radar segue a LGPD (Lei nº 13.709/2018).

## Princípios

1. **Read-only** — nenhuma ferramenta altera dados na origem.
2. **Mínimo necessário** — só os dados que a ferramenta pede.
3. **Você no controle** — desconectar / excluir conta a qualquer momento em `app.mcp.ai`.

## Sub-processadores

| Sub-processador | País | Papel |
|---|---|---|
| **adsb.lol (rede comunitária ADS-B)** | NL | fonte open data (ODbL 1.0) das posições ao vivo de aeronaves |
| **OurAirports** | CA | base pública (domínio público) de aeroportos usada no lookup offline por código |
| **mwgg/Airports (GitHub)** | US | base MIT de aeroportos (ICAO/timezone) usada no lookup offline por código |
| **LLM host escolhido por você** (Claude, ChatGPT, Cursor, agente próprio) | varia | Consumidor dos dados |

> ⚠️ O LLM host que você escolher é um sub-processador **fora do nosso controle**. Os dados retornados pelas tools são enviados pra ele a cada chamada. Recomendamos planos com opt-out de treinamento.

## Seus direitos (LGPD)

Acessar, corrigir, eliminar, portar, revogar consentimento. Contato: [flightradar@mcp.ai](mailto:flightradar@mcp.ai). Reclamações: [ANPD](https://www.gov.br/anpd/pt-br).

**Última atualização**: 2026-06-10.
