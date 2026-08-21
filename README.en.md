# Flight Radar

### Flight Radar for Claude, ChatGPT and AI agents

Live flight radar: real-time position of any aircraft transmitting ADS-B right now. Search by registration, ICAO hex or callsign, see traffic within a radius of any point (sorted by distance), find out which plane is flying over you, list aircraft by type (A320, 737, PC-12) or military aircraft airborne. Includes airport lookup by IATA/ICAO code, offline base with ~90k airports with city, country, coordinates and timezone. Data from the adsb.lol community network (best coverage in urban areas). No credentials, platform-hosted.

- 📊 **6 tools**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Flight Radar`, URL `https://api.mcp.ai/p_flightradar`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=flightradar&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9mbGlnaHRyYWRhciJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=flightradar&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_flightradar%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_flightradar
```

---

## 6 tools

| Tool | Description |
|---|---|
| `flightradar_aircraft` | Posição ao vivo de aeronaves específicas, por matrícula (registration), código hex ICAO 24-bit e/ou callsign. |
| `flightradar_nearby` | Aeronaves transmitindo ADS-B agora num raio (em milhas náuticas) de um ponto, ordenadas da mais próxima pra mais distante. |
| `flightradar_closest` | A aeronave mais próxima de um ponto (dentro do raio em milhas náuticas). |
| `flightradar_type` | Aeronaves de um tipo ICAO especifico transmitindo agora no mundo (ex.: PC12 = Pilatus PC-12, E195 = Embraer 195, AS50 = Esquilo). |
| `flightradar_military` | Aeronaves militares transmitindo ADS-B agora no mundo. |
| `flightradar_airport` | Informações de aeroportos por código IATA, ICAO, GPS ou local (aceita vários códigos numa chamada). |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_flightradar` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
