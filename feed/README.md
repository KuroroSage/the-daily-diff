# The Daily Diff — feed

This directory is the published artifact: one signed edition per weekday under
`YYYY/MM/DD/feed.json` (+ detached `.sig`), a signed `revocations.json` kill switch,
and the publisher public key (`keys/feed.pub`). The public web mirror is generated
from it by [`apps/diff-web`](../apps/diff-web) — fail-closed: only editions whose
signatures verify against the client's trust root are ever rendered.

**Destiny:** its own public GitHub repo with branch protection + required review — that
infrastructure *is* the two-human rule, the append-only audit log, the tamper evidence,
and the CDN (spec §3). During founder-dogfood it lives here and clients read it via a
local path.

Clients pin the publisher key at build time; they verify the feed signature, every
action's individual signature, and the revocation list before rendering anything, and
fail closed on all of it. Nothing in this directory can grant itself new powers — the
allowlist and grammar live compiled into the client.
