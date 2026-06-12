# futu-proxy-rules

Surge and Shadowrocket rule sets for Futu, Moomoo, and related domains.

## Rule Set

This repository currently includes rules for the following domain suffixes:

```text
moomoo.com
futuhn.com
futustatic.com
futunn.com
````

## Usage

### Surge

Add the following rule to the `[Rule]` section of your Surge configuration:

```ini
RULE-SET,https://raw.githubusercontent.com/chaiyanlin/futu-proxy-rules/refs/heads/main/Futu.list,DIRECT
```

If you want these domains to go through a proxy policy instead, replace `DIRECT` with your own policy name, for example:

```ini
RULE-SET,https://raw.githubusercontent.com/chaiyanlin/futu-proxy-rules/refs/heads/main/Futu.list,PROXY
```

### Shadowrocket

Add the following rule to the `[Rule]` section of your Shadowrocket configuration:

```ini
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/rules/Futu.list,DIRECT
```

Make sure the rule is placed before the final fallback rule, for example:

```
[Rule]
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/rules/Futu.list,DIRECT
FINAL,PROXY
```

## Rule File Format

The rule file is located at:

```text
rules/Futu.list
```

Each line contains only the rule itself, without any policy such as `DIRECT` or `PROXY`.

Example:

```ini
DOMAIN-SUFFIX,moomoo.com
DOMAIN-SUFFIX,futuhn.com
DOMAIN-SUFFIX,futustatic.com
DOMAIN-SUFFIX,futunn.com
```

The policy is defined when the rule set is referenced:

```
RULE-SET,https://raw.githubusercontent.com/andychai199026/futu-proxy-rules/main/rules/Futu.list,DIRECT
```

## License

MIT

