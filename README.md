# France Business Sales Notices (BODACC, companies)

[![Apify Actor](https://img.shields.io/badge/Apify-Actor-1f6feb)](https://apify.com/phonic_lily/france-business-sales-bodacc) ![Licence](https://img.shields.io/badge/licence-Licence_Ouverte_2.0-blue) ![Records](https://img.shields.io/badge/records-82%2C690-green)

Search French business and going-concern sale notices (cessions de fonds de commerce) published in the BODACC, where the buyer is a legal entity: date, court registry, buyer SIREN and name, activity sold, location and stated sale price. No individuals. Embedded data, pay per record.

## What you get
- **82,690 records**, each carrying its own `license` and `attribution` fields, ready to republish with the required credit.
- A **100-record free sample** in this repository: [`sample.jsonl`](sample.jsonl) and [`sample.csv`](sample.csv) (opens as a table on GitHub).
- The **full dataset** as a filterable API (JSON, CSV, Excel), no scraping, no login: [France Business Sales Notices (BODACC, companies) on Apify](https://apify.com/phonic_lily/france-business-sales-bodacc).

## One record
```json
{
  "notice_id": "A202602191146",
  "publication_date": "2026-11-15",
  "court_registry": "Greffe du Tribunal de Commerce d'Amiens",
  "buyer_siren": "345130488",
  "buyer_name": "CARREFOUR PROXIMITE FRANCE",
  "buyer_legal_form": "Société par Actions Simplifiée",
  "buyer_naf": "77.40Z",
  "city": "Mondeville, Amiens",
  "postal_code": "14120, 80000",
  "department": "80",
  "category": "Achat d'un établissement secondaire ou complémentaire par une personne morale",
  "sale_price_eur": 365000.0
}
```

## Quick start
Python:
```python
from apify_client import ApifyClient
client = ApifyClient('<YOUR_APIFY_TOKEN>')
run = client.actor('phonic_lily/france-business-sales-bodacc').call(run_input={'maxResults': 10})
for item in client.dataset(run['defaultDatasetId']).iterate_items():
    print(item)
```
Or from the command line:
```bash
curl -X POST 'https://api.apify.com/v2/acts/phonic_lily~france-business-sales-bodacc/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>' \
  -H 'Content-Type: application/json' -d '{"maxResults": 10}'
```
Pricing is pay-per-record on Apify (see the Actor page); the sample here is free.

## Fields
| Field | Description |
|---|---|
| `notice_id` | BODACC notice id. |
| `publication_date` | Publication date (ISO). |
| `court_registry` | Commercial court registry. |
| `buyer_siren` | Buyer SIREN. |
| `buyer_name` | Buyer legal name. |
| `buyer_legal_form` | Buyer legal form as printed. |
| `buyer_naf` | Buyer NAF code when known, else null. |
| `city` | City. |
| `postal_code` | Postal code. |
| `department` | Department code. |
| `category` | Sale category. |
| `sale_price_eur` | Stated sale price in EUR, null when not stated. |
| `activity` | Activity of the business sold (first 400 chars). |

## Data, licence and attribution
BODACC 'ventes et cessions' notices published by DILA under Licence Ouverte 2.0, publication dates 2023-07 to 2026-07, duplicates removed. Only notices whose buyer is a legal entity (personne morale) are kept; every notice involving a natural person is excluded. Seller / previous owner data and managers' names are not included. Sale price is the price stipulated in the notice (null when not stated, never 0). Activity text is dropped when it names a person.

**Licence:** Licence Ouverte 2.0 (Etalab)

**Attribution:** Source: DILA, BODACC (Bulletin officiel des annonces civiles et commerciales), Licence Ouverte 2.0 (Etalab).

Snapshot date: 2026-11-15. Empty values are `null`, never 0.

## Cite this dataset
GitHub's *Cite this repository* button reads [`CITATION.cff`](CITATION.cff).

## Related
Business-sale prices and market analysis for French businesses, by sector and department, are browsable on [Le Registre (cessiondefonds.com)](https://cessiondefonds.com/).

## Feedback
Found an error or want a field added? Open an issue in this repository.
