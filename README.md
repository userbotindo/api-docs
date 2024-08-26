# Userbotindo API Service

## Table of Contents

- [General API Information](#general-api-information)
- [Services](#services)
  - [Spam Detetion](#spam-detection)
    - [Predict](#predict)
    - [Preprocess](#preprocess)
- [More Information](#more-information)

## General API Information

- All API endpoints base url are

```
https://api.userbotindo.com
```

- All endpoints return a JSON Object

- every endpoint uses API key for authentication. You can get the API key by sending `/token` to [@dAnjani_bot](https://t.me/dAnjani_bot) on Telegram. API key is required to be sent as `x-api-key` header.

```
curl -X 'POST' \
  'https://api.userbotindo.com/<SERVICE_ENDPOINT>' \
  -H 'accept: application/json' \
  -H 'x-api-key: '<YOUR_API_KEY>' \
  -H 'Content-Type: application/json'
}'
```

## Services

### Spam Detection

#### Predict

Run a spam detection on the given text. This endpoint will do text preprocess first before running the spam detection. You don't need to call preprocess endpoint before calling this endpoint.

```
POST /v1/spam-detection/predict
```

Example request body:

```json
{
  "text": "string"
}
```

Example response:

```json
{
  "message": "successfuly done spam detection",
  "data": {
    "input_text": "string",
    "processed_text": "string",
    "text_length": 0,
    "word_count": 0,
    "language": {
      "language": "string",
      "probability": 0,
      "is_reliable": true
    },
    "prediction": {
      "is_spam": true,
      "ham_score": 0,
      "spam_score": 0
    },
    "error_code": "FAIL_ON_1"
  }
}
```

#### Preprocess

Run a text preprocess on the given text.

> Note: If you're intended to run spam detection, **NO NEED** to call this endpoint. Spam detection endpoint will automatically run preprocess under the hood.

```
POST /v1/spam-detection/preprocess
```

Example request body:

```json
{
  "text": "string"
}
```

Example response:

```json
{
  "message": "successfuly done text preprocess",
  "data": {
    "input_text": "string",
    "processed_text": "string",
    "text_length": 0,
    "word_count": 0,
    "language": {
      "language": "string",
      "probability": 0,
      "is_reliable": true
    }
  }
}
```

## More Information

- [Spam Detection Service Announcement](https://t.me/SpamPredictionLog/25)
- [Userbotindo](https://t.me/userbotindo)
- [Anjani](https://t.me/dAnjani_bot)

## Privacy Policy

API Service complies with the [Userbotindo Privacy Policy](https://userbotindo.com/privacy).
