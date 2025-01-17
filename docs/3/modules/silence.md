---
title: Module Details (silence)
---

## The "silence" Module

### Description

This module adds the `/SILENCE` command which allows users to ignore other users on server-side.

### Configuration

To load this module use the following `<module>` tag:

```xml
<module name="silence">
```

#### `<silence>`

The `<silence>` tag defines settings about how the silence module should behave. This tag can only be defined once.

Name        | Type    | Default Value  | Description
----------- | ------- | -------------- | -----------
exemptuline | Boolean | Yes            | Whether services on U-lined servers are exempt from silences.
maxentries  | Number  | 32             | The maximum number of entries that can be on a `/SILENCE` list.

#### Example Usage

```xml
<silence exemptuline="yes"
         maxentries="32">
```

### Commands

Name    | Parameter Count | Syntax                    | Description
------- | --------------- | ------------------------- | -----------
SILENCE | 1-2             | `[(+|-)<mask> [<flags>]]` | Allows users to add users to their `/SILENCE` list, remove users from their `/SILENCE` list, and list users on their `/SILENCE` list.

The flags in the second parameter should be set to one of the following values:

Flag | Description
---- | -----------
C    | Matches a CTCP targeted at a user.
c    | Matches a CTCP targeted at a channel.
d    | Default behaviour; equivalent to CciNnPpTt.
i    | Matches an invite to a channel.
N    | Matches a NOTICE targeted at a user.
n    | Matches a NOTICE targeted at a channel.
P    | Matches a PRIVMSG targeted at a user.
p    | Matches a PRIVMSG targeted at a channel.
T    | Matches a TAGMSG targeted at a user.
t    | Matches a TAGMSG targeted at a channel.
x    | Exempt the mask from silence rules.

#### Example Usage

Adds a `/SILENCE` entry which blocks all possible messages from users matching `*!*@example.com`:

```plaintext
/SILENCE *!*@example.com
```

Removes a `/SILENCE` entry which blocked private `NOTICE`, `PRIVMSG`, and `TAGMSG` messages from users matching `*!*@example.com`:

```plaintext
/SILENCE *!*@example.com NPT
```

View all entries on the `/SILENCE` list:

```plaintext
/SILENCE
```
