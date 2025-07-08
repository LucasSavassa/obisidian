from [Digital Identity Guidelines | NIST Special Publication](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf)

| Requirement Category         | NIST Recommendation                        |
| ---------------------------- | ------------------------------------------ |
| **Minimum length**           | 8 chars (user), 6 chars (system)           |
| **Encourage longer phrases** | 15+ chars recommended                      |
| **Max length**               | Support up to 64 chars                     |
| **Allowed characters**       | ASCII, space, Unicode (with normalization) |
| **Blocklists required**      | Must reject common/compromised passwords   |
| **Complexity rules**         | Remove all composition mandates            |
| **Periodic changes**         | Only on compromise                         |
| **Password hints/KBA**       | Disallowed                                 |
| **Full verification**        | No truncation                              |
| **Support paste/show**       | Encouraged                                 |
| **Rate limit failures**      | Mandatory                                  |
