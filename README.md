# Flight Radar

### Flight Radar para Claude, ChatGPT e agentes de IA

Radar de voos ao vivo: posição em tempo real de qualquer aeronave transmitindo ADS-B agora. Busque por matrícula, hex ICAO ou callsign, veja o tráfego num raio de qualquer ponto (ordenado por distância), descubra qual avião está passando em cima de você, liste aeronaves por tipo (A320, 737, PC-12) ou militares no ar. Inclui consulta de aeroportos por código IATA/ICAO, base offline com ~90 mil aeroportos com cidade, país, coordenadas e fuso. Dados da rede comunitária adsb.lol (cobertura maior em áreas urbanas). Sem credencial, hospedado pela plataforma.

- 📊 **6 ferramentas**
- 🔒 **Somente leitura**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Flight Radar` e **URL** `https://api.mcp.ai/p_flightradar`.

### Cursor

[➕ Instalar Flight Radar no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=flightradar&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9mbGlnaHRyYWRhciJ9)

### VS Code (Copilot Chat)

[➕ Instalar Flight Radar no VS Code](vscode:mcp/install?name=flightradar&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_flightradar%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_flightradar
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Que avião está passando em cima de mim agora?
Onde está a aeronave PR-GUO?
Quantos aviões estão sobrevoando São Paulo num raio de 30 milhas?
```

---

## 6 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `flightradar_aircraft` | Posição ao vivo de aeronaves específicas, por matrícula (registration), código hex ICAO 24-bit e/ou callsign. |
| `flightradar_nearby` | Aeronaves transmitindo ADS-B agora num raio (em milhas náuticas) de um ponto, ordenadas da mais próxima pra mais distante. |
| `flightradar_closest` | A aeronave mais próxima de um ponto (dentro do raio em milhas náuticas). |
| `flightradar_type` | Aeronaves de um tipo ICAO especifico transmitindo agora no mundo (ex.: PC12 = Pilatus PC-12, E195 = Embraer 195, AS50 = Esquilo). |
| `flightradar_military` | Aeronaves militares transmitindo ADS-B agora no mundo. |
| `flightradar_airport` | Informações de aeroportos por código IATA, ICAO, GPS ou local (aceita vários códigos numa chamada). |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Planos a partir do tier grátis. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: adsb.lol (rede comunitária ADS-B), OurAirports, mwgg/Airports (GitHub), o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_flightradar`.


---

## Suporte

- 📧 [flightradar@mcp.ai](mailto:flightradar@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/flightradar-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_flightradar` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
