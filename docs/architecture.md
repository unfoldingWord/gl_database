# GL Pipeline architecture

## Phase 1: Build initial pipeline

1) An update is triggered

- To begin with, the update can be a manual action
- In the future, the update might be run via scheduled task or from an outside data source

2) Download data

- Initially, the import data will be files committed into the data repository
- In the future, data files may be specified in a manifest (see notes about triggers above)

3) Import data

- Create an internal data model for processing, current sources are:
  - The export from tD
  - The Phase Data from Clickup
- Data model could be done in-memory or with a transient SQLite database
- Suggest using Django for a data model, but could also use something like [Luigi](https://github.com/spotify/luigi)

4) Export data

- Obsidian / graph
- CSV suitable for loading into Flourish

## Phase 2: Expand pipeline

- Add additional imports
  - progress.Bible
  - Joshua Project data
- Add additional exports
  - Generate langnames.json and Deploy to Netlify
  - Static site
    - Built with suggested tools (Docsify, Stork)
    - Deploy to Netlify

## Suggested structure

```
├── LICENSE
├── README.md
├── data
│   ├── inputs
│   └── outputs
├── pipeline
│   └── src
└── site
    └── src
```
