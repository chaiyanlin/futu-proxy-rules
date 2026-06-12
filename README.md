# futu-proxy-rules

Surge and Shadowrocket rule sets for Futu, Moomoo, and related domains.

## Files

```text
.
├── Futu.list
├── Futu_Extended.list
└── README.md
````

### `Futu.list`

Core domain suffix rules for Futu and Moomoo.

This is the recommended rule set for most users.

Raw URL:

```text
https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list
```

### `Futu_Extended.list`

Extended rules for Futu and Moomoo, including additional auxiliary domains and IP-CIDR rules.

Use this file only when `Futu.list` is not enough, for example when some app features, quotes, trading endpoints, or push connections still do not work as expected.

Raw URL:

```text
https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu_Extended.list
```

## Usage

### Surge

Add the following rules to the `[Rule]` section of your Surge configuration:

```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list,DIRECT
FINAL,PROXY
```

To also enable the extended rule set:

```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list,DIRECT
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu_Extended.list,DIRECT
FINAL,PROXY
```

Replace `DIRECT` with your own policy name if you want these domains or IP ranges to go through a proxy policy.

Example:

```ini
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list,PROXY
```

### Shadowrocket

Add the following rules to the `[Rule]` section of your Shadowrocket configuration:

```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list,DIRECT
FINAL,PROXY
```

To also enable the extended rule set:

```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list,DIRECT
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu_Extended.list,DIRECT
FINAL,PROXY
```

Make sure these rules are placed before the final fallback rule, such as `FINAL,PROXY`.

## Rule File Format

The rule files are standard rule-set files.

Each line contains only the rule itself, without any policy such as `DIRECT`, `PROXY`, or other policy group names.

Example:

```ini
DOMAIN-SUFFIX,moomoo.com
DOMAIN-SUFFIX,futunn.com
IP-CIDR,1.14.242.0/23,no-resolve
```

The policy is defined when the rule set is referenced:

```ini
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list,DIRECT
```

## Recommendation

For most users:

```ini
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list,DIRECT
```

For users who need broader coverage:

```ini
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu.list,DIRECT
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/Futu_Extended.list,DIRECT
```

## License

MIT
