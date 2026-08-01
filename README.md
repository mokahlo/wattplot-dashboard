# Wattplot — Live Dashboard

Interactive dashboard for the [wattplot smart-folding planter](https://github.com/mokahlo/wattplot).
Self-contained HTML + JS, subscribes to MQTT-over-WebSockets and overlays live data on a
24h sun-position sim.

**[Live demo](https://mokahlo.github.io/wattplot-dashboard/)** — runs in demo/sim mode by default.

## URL parameters (all optional)

| Param | Default | Notes |
|---|---|---|
| `?live=1` | off | Enable MQTT connection |
| `?broker=host:port` | `ws://192.168.68.72:9001` | WebSocket broker |
| `?user=name` | `wattplot` | MQTT username |
| `?pass=password` | — | MQTT password |
| `?prefix=wattplot` | `wattplot` | Topic prefix |

### Local use (LAN live data)

The simplest local flow — open the file from disk with the live flag:

```
file:///C:/dev/wattplot/booth/sim_dashboard.html?live=1
```

The defaults point at the wattplot LAN broker (`192.168.68.72:9001`) with the
standard `wattplot` user. To use a different broker, override via `?broker=…&user=…&pass=…`.

### What the sim does

- 24h scrubber (00:00 → 24:00, Phoenix AZ 33.45°N)
- POA irradiance from solar geometry + a 620 W bifacial panel model
- Bed DLI accumulation, soil drain, battery SOC, panel temperature, wind
- Decision logic for panel tilt (storm fold / preemptive / wring-out / power)
- All values derive from `wattplot_params.py` constants — same model the device uses

## File layout

```
index.html       — the whole dashboard (HTML + CSS + JS, 41 KB)
README.md        — this file
```

## License

Wattplot project — see [mokahlo/wattplot](https://github.com/mokahlo/wattplot).
