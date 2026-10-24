# Cybersecurity Portfolio

Hands-on security labs documented by **Younes Chemmaoui**, final-year Computer Engineering student (EMSI) specializing in infrastructure and network security.

Each write-up follows the same structure: **reconnaissance → access → finding → mistakes made → defensive takeaway.** The goal is not only to solve the box, but to understand how the same weakness would be detected and prevented in a real environment.

## Labs

| Platform | Box | Topic | Write-up |
|----------|-----|-------|----------|
| HackTheBox, Starting Point | Redeemer | Unauthenticated Redis exposed on 6379 | [Read](labs/hackthebox/starting-point/Redeemer/README.md) |

## Structure

```
labs/
└── hackthebox/
    └── starting-point/
        └── <box>/
            ├── README.md   # clean write-up
            └── notes/      # raw working notes
```

## Rules I follow
- Flags and credentials are never published.
- Only legal, authorized lab environments.
