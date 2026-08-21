# Ferramentas

Flight Radar expõe 6 ferramentas (todas somente leitura).

### 1. `flightradar_aircraft`
**Input**: `registrations` (opcional), `hexes` (opcional), `callsigns` (opcional)

Posição ao vivo de aeronaves específicas, por matrícula (registration), código hex ICAO 24-bit e/ou callsign.

### 2. `flightradar_nearby`
**Input**: `lat`, `lon`, `radius_nm` (opcional), `limit` (opcional)

Aeronaves transmitindo ADS-B agora num raio (em milhas náuticas) de um ponto, ordenadas da mais próxima pra mais distante.

### 3. `flightradar_closest`
**Input**: `lat`, `lon`, `radius_nm` (opcional)

A aeronave mais próxima de um ponto (dentro do raio em milhas náuticas).

### 4. `flightradar_type`
**Input**: `type`, `limit` (opcional)

Aeronaves de um tipo ICAO especifico transmitindo agora no mundo (ex.: PC12 = Pilatus PC-12, E195 = Embraer 195, AS50 = Esquilo).

### 5. `flightradar_military`
**Input**: `limit` (opcional)

Aeronaves militares transmitindo ADS-B agora no mundo.

### 6. `flightradar_airport`
**Input**: `codes`

Informações de aeroportos por código IATA, ICAO, GPS ou local (aceita vários códigos numa chamada).

## Prompts de exemplo

```
Que avião está passando em cima de mim agora?
Onde está a aeronave PR-GUO?
Quantos aviões estão sobrevoando São Paulo num raio de 30 milhas?
```
