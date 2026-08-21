---
name: flightradar-mcp
description: Skill da REST API do Flight Radar na MCP.AI: 6 endpoints em /api/flightradar. Radar de voos ao vivo: posição em tempo real de qualquer aeronave transmitindo ADS-B agora. Busque por matrícula, hex ICAO ou callsign, veja o tráfego num raio de qualquer ponto (ordenado por distância), descubra qual avião está passando em cima de você, liste aeronaves por tipo (A320, 737, PC-12) ou militares no ar. Inclui consulta de aeroportos por código IATA/ICAO, base offline com ~90 mil aeroportos com cidade, país, coordenadas e fuso. Dados da rede comunitária adsb.lol (cobertura maior em áreas urbanas). Sem credencial, hospedado pela plataforma. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Flight Radar — REST API skill

Você tem acesso à **Flight Radar** REST API na MCP.AI.

> Radar de voos ao vivo: posição em tempo real de qualquer aeronave transmitindo ADS-B agora. Busque por matrícula, hex ICAO ou callsign, veja o tráfego num raio de qualquer ponto (ordenado por distância), descubra qual avião está passando em cima de você, liste aeronaves por tipo (A320, 737, PC-12) ou militares no ar. Inclui consulta de aeroportos por código IATA/ICAO, base offline com ~90 mil aeroportos com cidade, país, coordenadas e fuso. Dados da rede comunitária adsb.lol (cobertura maior em áreas urbanas). Sem credencial, hospedado pela plataforma.

## Base URL

```
https://api.mcp.ai/api/flightradar
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/flightradar/aircraft \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/flightradar/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (6)

#### `flightradar_aircraft`

Posição ao vivo de aeronaves específicas, por matrícula (registration), código hex ICAO 24-bit e/ou callsign. _(POST /api/flightradar/aircraft)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `registrations` | string[] | Não | Matrículas (tail numbers), ex.: ["PR-GUO", "PS-BOS", "N12345"]. |
| `hexes` | string[] | Não | Códigos hex ICAO 24-bit do transponder, ex.: ["e80453"]. |
| `callsigns` | string[] | Não | Callsigns do voo, ex.: ["GLO1740", "TAM3456"]. |

#### `flightradar_airport`

Informações de aeroportos por código IATA, ICAO, GPS ou local (aceita vários códigos numa chamada). _(POST /api/flightradar/airport)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `codes` | string[] | Sim | Códigos de aeroporto (IATA 3 letras, ICAO 4, GPS ou local). Ex.: ["GRU", "SBCG", "KJFK"]. Máx. 50. |

#### `flightradar_closest`

A aeronave mais próxima de um ponto (dentro do raio em milhas náuticas). _(POST /api/flightradar/closest)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `lat` | number | Sim | Latitude do centro (-90 a 90). |
| `lon` | number | Sim | Longitude do centro (-180 a 180). |
| `radius_nm` | number | Não | Raio máximo de busca em milhas náuticas (1 a 250; default 100). |

#### `flightradar_military`

Aeronaves militares transmitindo ADS-B agora no mundo. _(POST /api/flightradar/military)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `limit` | integer | Não | Máximo de aeronaves no retorno (1 a 250; default 50). |

#### `flightradar_nearby`

Aeronaves transmitindo ADS-B agora num raio (em milhas náuticas) de um ponto, ordenadas da mais próxima pra mais distante. _(POST /api/flightradar/nearby)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `lat` | number | Sim | Latitude do centro (-90 a 90). |
| `lon` | number | Sim | Longitude do centro (-180 a 180). |
| `radius_nm` | number | Não | Raio em milhas náuticas (1 a 250; default 50). |
| `limit` | integer | Não | Máximo de aeronaves no retorno (1 a 250; default 50). |

#### `flightradar_type`

Aeronaves de um tipo ICAO especifico transmitindo agora no mundo (ex.: PC12 = Pilatus PC-12, E195 = Embraer 195, AS50 = Esquilo). _(POST /api/flightradar/type)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `type` | string | Sim | Código ICAO do tipo de aeronave, ex.: A320, A20N, B738, E195, PC12, C172. |
| `limit` | integer | Não | Máximo de aeronaves no retorno (1 a 250; default 50). |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_flightradar` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
