# clinical-decision-support

clinical-decision-support — domain: ehr

- **Port:** 8312
- **Language:** Python 3.11 + Flask
- **Database:** `ehr` (Postgres, table `clinical_decision_support`)
- **Event bus:** Kafka

## API

| Method    | Path                       |
|-----------|----------------------------|
| GET       | `/api/clinical_decision_support/`          |
| POST      | `/api/clinical_decision_support/`          |
| GET       | `/api/clinical_decision_support/<id>`      |
| PUT/PATCH | `/api/clinical_decision_support/<id>`      |
| DELETE    | `/api/clinical_decision_support/<id>`      |
| GET       | `/health`                  |
| GET       | `/ready`                   |

## Events

**Publishes:** (none)
**Subscribes:** lab.result.available, encounter.started

## HTTP peer dependencies

- `ehr-service`
- `ai-invocations-service`
- `drug-interactions-service`
- `audit-log-service`

## Local dev

```bash
pip install -e ../../libs/py-healthcare-common
pip install -r requirements.txt
cp .env.example .env
(cd ../../infra && docker compose up -d postgres kafka kafka-init)
python -m app.main
```

## Tests

```bash
pytest
```
