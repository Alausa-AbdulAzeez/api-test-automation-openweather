# OpenWeatherMap API Test Cases

## Base URL
```
https://api.openweathermap.org/data/2.5
```

## Test Suite: Weather API Endpoints

| Test ID | Test Case                    | Endpoint   | Query Parameters                    | Expected Response    |
| ------- | ---------------------------- | ---------- | ----------------------------------- | ------------------ |
| TC-01   | Valid city returns 200       | `/weather` | `q=London`<br>`appid={{API_KEY}}`   | `200` , `name = London`          |
| TC-02   | Invalid city name            | `/weather` | `q=abgdg`<br>`appid={{API_KEY}}`    | `404`, `No city info should be returned`    |
| TC-03   | Empty city name              | `/weather` | `q=`<br>`appid={{API_KEY}}`         | `4**`, `No city info should be returned`  |
| TC-04   | Invalid API key              | `/weather` | `q=London`<br>`appid=AAAASJJg`      | `401`, `No city info should be returned` |
| TC-05   | Missing API key              | `/weather` | `q=London`<br>`appid=`              | `401`, `No city info should be returned` |
| TC-06   | Valid city ID returns 200    | `/weather` | `id=2172797`<br>`appid={{API_KEY}}` | `200`, `id = 2172797`          |
| TC-07   | Invalid city ID              | `/weather` | `id=12445`<br>`appid={{API_KEY}}`   | `404`,  `No city info should be returned`    |
| TC-08   | Empty city ID                | `/weather` | `id=`<br>`appid={{API_KEY}}`        | `4**`, `No city info should be returned`  |
| TC-09   | Invalid API key with city ID | `/weather` | `id=2172797`<br>`appid=112244`      | `4**`, `No city info should be returned` |
| TC-10   | Missing API key with city ID | `/weather` | `id=2172797`<br>`appid=`            | `4**`, `No city info should be returned` |

