---
id: ory-import-oauth2-client
title: ory import oauth2-client
description: ory import oauth2-client Import one or more OAuth 2.0 Clients from files or STDIN
---

<!--
This file is auto-generated.

To improve this file please make your change against the appropriate "./cmd/*.go" file.
-->
## ory import oauth2-client

Import one or more OAuth 2.0 Clients from files or STDIN

### Synopsis

This command reads in each listed JSON file and imports their contents as a list of OAuth 2.0 Clients.

The format for the JSON file is:

[
  {
    "client_secret": "...",
    // ... all other fields of the OAuth 2.0 Client model are allowed here
  }
]

Please be aware that this command does not update existing clients. If the client exists already, this command will fail.

```
ory import oauth2-client <file-1.json> [<file-2.json> ...] [flags]
```

### Examples

```
Import an example OAuth2 Client:
	cat > ./file.json <<EOF
	[
      {
	    "grant_types": ["implicit"],
	    "scope": "openid"
	  },
      {
	    "grant_types": ["authorize_code"],
	    "scope": "openid"
	  }
    ]
	EOF

	{{ .CommandPath }} file.json

Alternatively:

	cat file.json | {{ .CommandPath }}

To encrypt an auto-generated OAuth2 Client Secret, use flags `--pgp-key`, `--pgp-key-url` or `--keybase` flag, for example:

  {{ .CommandPath }} -n "my app" -g client_credentials -r token -a core,foobar --keybase keybase_username

```

### Options

```
      --format string        Set the output format. One of table, json, yaml, json-pretty, and jsonpath. (default "default")
  -h, --help                 help for oauth2-client
      --keybase string       Keybase username for encrypting client secret.
      --pgp-key string       Base64 encoded PGP encryption key for encrypting client secret.
      --pgp-key-url string   PGP encryption key URL for encrypting client secret.
      --project string       The project to use
  -q, --quiet                Be quiet with output printing.
```

### Options inherited from parent commands

```
  -c, --config string   Path to the Ory Network configuration file.
  -y, --yes             Confirm all dialogs with yes.
```

### SEE ALSO

* [ory import](ory-import)	 - Import resources

