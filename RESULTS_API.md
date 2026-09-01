# MOA 2026 Kernel Leaderboard Results API

## Send a result

```text
POST https://micro2026-api.duckdns.org/api/results
```

Headers:

```text
Content-Type: application/json
x-api-key: <shared API key>
```

Body:

```json
{
  "teamName": "Team Orion",
  "kernelName": "ops::sliding_project_qkv",
  "score": 98.4,
  "buildability": true,
  "correctness": true,
  "performance": 1432.8
}
```

All fields are required.

| Field | Type | Notes |
| --- | --- | --- |
| `teamName` | string | Team name |
| `kernelName` | string | One of the kernel names below |
| `score` | number | Benchmark score |
| `buildability` | boolean | Use `true` or `false`, not strings |
| `correctness` | boolean | Use `true` or `false`, not strings |
| `performance` | number | Higher is better |

Allowed kernel names:

```text
ops::sliding_project_qkv
ops::sliding_attention_output
ops::decoder_feedforward
```

## Temporary ranking logic

This is temporary and may change later.

1. Results are ranked separately for each kernel.
2. Only one result per team and kernel is displayed.
3. If a team has any result with both `buildability: true` and `correctness: true`, its best such result is used.
4. Teams without a fully valid result are listed below all fully valid teams.
5. Within the same group, higher `performance` ranks higher. Ties use earlier submission time.

## Example

```bash
curl -X POST 'https://micro2026-api.duckdns.org/api/results' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <shared API key>' \
  -d '{
    "teamName":"Team Orion",
    "kernelName":"ops::sliding_project_qkv",
    "score":98.4,
    "buildability":true,
    "correctness":true,
    "performance":1432.8
  }'
```
