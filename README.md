# OpenPick

**India-first electronics recommendation engine** for laptops, smartphones, monitors and headphones.

OpenPick is a local-first MVP. It lets you create products manually, import CSV/JSON, define custom requirements, rank products with transparent weighted scoring, compare options, and record price observations in INR.

## Current MVP capabilities

- Four categories: laptops, smartphones, monitors and headphones
- Search by product, brand, model and specification text
- Budget filtering in INR
- Must-have and weighted preference criteria
- Transparent match score with criteria breakdown
- Product comparison selection
- Manual product creation
- CSV and JSON import with validation
- Local persistence in browser storage
- Explicit source, timestamp and price verification status
- No fake live deals and no mandatory API keys

## Important data limitations

This starter does **not** claim to have live retailer price feeds. Product records are clearly labelled as demo data or user-entered/imported data. A retailer link is not proof of current price or availability.

There is no universal free API that reliably provides complete, current prices for all Indian electronics retailers. Add official or authorized APIs only after checking access eligibility, terms, attribution, caching restrictions and quotas.

All demo products are labelled `DEMO DATA` in the interface and are not live offers. Remove them from the catalogue when you are ready to use only your own records.

## Requirements

- Node.js 20 or newer recommended
- npm
- Git

## Run locally

```bash
npm install
npm run dev
```

Open the local URL printed by Vite.

## Production build

```bash
npm run build
npm run preview
```

## Tests

```bash
npm test
```

## Upload to GitHub

1. Create a new repository called `openpick` on GitHub.
2. Extract this project ZIP.
3. Open the extracted `openpick` folder in VS Code.
4. Open a terminal in that folder and run:

```bash
git init
git add .
git commit -m "Initial OpenPick MVP"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/openpick.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username. If GitHub already initialized the repository with a README, either create an empty repository or pull/merge its initial commit first.

## Free deployment with Cloudflare Pages

1. Push the project to GitHub.
2. In Cloudflare, open **Workers & Pages** and create a Pages project connected to the repository.
3. Framework preset: **Vite**.
4. Build command: `npm run build`.
5. Build output directory: `dist`.
6. Deploy. The site will receive a `pages.dev` address.

The app is static and does not require a backend for the current MVP. Local saved data stays in each browser and does not sync between devices.

## CSV import format

Recommended column headers:

```csv
category,brand,model,priceINR,retailer,productUrl,sourceType,observedAt,verificationStatus,notes
laptop,Example,Example Model,59999,Example Retailer,https://example.com/product,user-entered,2026-10-17T12:00:00Z,unverified,Replace with real data
```

Allowed categories: `laptop`, `smartphone`, `monitor`, `headphones`.

Prices are INR. Imports are treated as unverified unless the row explicitly provides a verification status; even then, do not use the verified label unless you have actually checked the source. The app preserves the supplied status and provenance.

## Architecture

- `src/types.ts`: core types
- `src/lib/scoring.ts`: deterministic ranking
- `src/lib/storage.ts`: browser persistence
- `src/lib/importers.ts`: CSV/JSON parsing and validation
- `src/data/demoProducts.ts`: explicitly labelled demo fixtures
- `src/App.tsx`: app shell and workflows

## Next steps

1. Replace or remove demo fixtures.
2. Add category-specific specification forms and stronger schema validation.
3. Add product-provider adapters for sources you are authorized to use.
4. Add price-history observations before making historical-low claims.
5. Add backend synchronization only if shared accounts are needed.

## License

MIT for this starter code. External datasets, product images, retailer content and provider APIs remain subject to their own licenses and terms.
