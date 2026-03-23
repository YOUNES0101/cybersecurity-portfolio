# Raw Notes — Redeemer

## Commands tried
- redis-cli 10.129.40.225 → failed (wrong syntax)
- redis-cli -h 10.129.40.225 -p 6379 → connected after VPN fix

## What worked
- ping → PONG (confirmed connection)
- info → got redis version 5.0.7, saw db0 has 4 keys
- select 0 → selected database 0
- keys * → listed: numb, temp, stor, flag
- get flag → "03e1d2b376c37ab3f5319922053953eb"

## Mistakes I made
- tried ls, list → not valid Redis commands
- tried select * index → wrong syntax, select takes only a number
- went into db[4] looking for flag → flag was in db0 all along

## Questions to research
- What is Redis used for in real applications?
- Why would Redis be exposed without authentication?
- What is the difference between Redis databases (0-15)?
