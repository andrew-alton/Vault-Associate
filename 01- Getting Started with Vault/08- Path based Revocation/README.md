## Lease Revocation Steps

There are two primary ways to revoke a lease in Vault.

| Lease Management Command | Description |
|-------------------------|-------------|
| `vault lease revoke my-lease-id` | Revokes a specific lease immediately. |
| `vault lease revoke -prefix aws/` | Revokes **all AWS access keys** issued under the `aws/` prefix. |

## Path-Based Revocation

Lease IDs in Vault are structured so that their **prefix always matches the path**
from which the secret was requested.

This design allows you to revoke **entire trees of secrets** at once instead of
revoking each lease individually.

### Example

To revoke **all AWS access keys** issued by Vault:

```bash
vault lease revoke -prefix aws/
