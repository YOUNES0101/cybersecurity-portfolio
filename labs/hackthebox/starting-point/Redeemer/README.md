# HackTheBox Starting Point: Redeemer

**Topic:** Redis exposed to the network without authentication
**Port:** 6379/tcp (Redis 5.0.7)

## 1. Connection
Connected through the HTB VPN, then reached the service with the Redis CLI:

```bash
redis-cli -h <target-ip> -p 6379
```

> My first attempt (`redis-cli <target-ip>`) failed: the host must be passed with `-h`.

## 2. Enumeration
```text
ping        -> PONG            # service answers, no authentication required
info        -> redis_version 5.0.7, keyspace: db0 has 4 keys
select 0    -> OK
keys *      -> numb, temp, stor, flag
get flag    -> <redacted>
```

## 3. Mistakes and what I learned
- `ls` / `list` are not Redis commands: Redis has its own command set (`keys`, `get`, `type`, `scan`).
- `select` takes a single database index (0 to 15 by default).
- I searched other databases first, while `info` already showed that only **db0** held keys. Read the enumeration output before guessing.

## 4. Defensive takeaway
How this would be prevented in production:
- Bind Redis to localhost or an internal interface only (`bind 127.0.0.1`).
- Keep `protected-mode yes` and require authentication (`requirepass` or Redis 6+ ACLs).
- Filter 6379/tcp at the firewall so it is never reachable from untrusted networks.
- Rename or disable dangerous commands (`FLUSHALL`, `CONFIG`).
- Alert on unexpected connections to the port from the SIEM.
