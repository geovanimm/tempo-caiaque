# Tempo Caiaque 🌬️🛶

App simples e estático que mostra, hora a hora, o vento (velocidade,
direção via seta e rajadas), a condição do tempo (ícone + temperatura)
e — quando o ponto é no mar/costa — a altura, direção e período das
ondas, para uma lista de coordenadas.

Sem build, sem backend: é um único `index.html` que consulta a API
gratuita da [Open-Meteo](https://open-meteo.com/) direto do navegador.

## Como adicionar/remover lugares

Edite o array `LUGARES` no `<script>` do `index.html`:

```js
const LUGARES = [
  { nome: "Represa das Palmeiras", lat: -26.6010169, lon: -49.3383111 },
  { nome: "Outro lugar", lat: -26.7889, lon: -48.6392 },
];
```

Não é preciso marcar se o lugar é mar ou não — o app tenta buscar dados
de ondas (API marítima da Open-Meteo) e só exibe esse bloco quando a
API retorna dados válidos para aquele ponto. Pontos em terra/represas
simplesmente não mostram ondas.

## Como funciona

- **Vento e tempo**: `api.open-meteo.com/v1/forecast` — velocidade
  (km/h) e direção (seta) do vento, rajadas, temperatura e condição do
  tempo (ícone), hora a hora.
- **Ondas**: `marine-api.open-meteo.com/v1/marine` — altura (m),
  direção e período, hora a hora, só quando disponível para o ponto.
- A página recarrega os dados automaticamente a cada 15 minutos.

## Publicar (GitHub Pages)

1. Repositório → **Settings → Pages**.
2. Em "Build and deployment", escolha **Deploy from a branch**.
3. Branch: `main`, pasta: `/ (root)`.
4. Salve — o app fica disponível em
   `https://geovanimm.github.io/tempo-caiaque/`.

Também funciona em qualquer outro host estático (Netlify, Vercel etc.)
— é só apontar para este repositório, sem comando de build.
