# Subpar

## MTA on-time performance visualization

An interactive chart of weekday on-time performance for each NYC subway line from 2015 to 2024.

Data sources:
* https://data.ny.gov/Transportation/MTA-Subway-Terminal-On-Time-Performance-2015-2019/f6rf-2a3t/about_data
* https://data.ny.gov/Transportation/MTA-Subway-Terminal-On-Time-Performance-Beginning-/vtvh-gimj/about_data

The 2015-2019 dataset does not include weekends, so I removed them from the 2020-2024 dataset to maintain the same metric.

## Production

~~http://jessechen.github.io/subpar/~~

## Dev Setup

```bash
npm install
npm run dev
```

## Deployment

```bash
npm run gh-pages
```

## License

MIT

## Building

To create a production build:

```bash
npm run build
```

You can preview the production build with `npm run preview`.
