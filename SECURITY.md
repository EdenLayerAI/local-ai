Security Policy

Supported Versions

EDEN uses a single public product version. The public version remains 1.0.0; internal security and migration revisions are tracked separately.

Version	Supported
1.0.0	:white_check_mark:
Other versions	:x:

Security fixes are applied to the supported 1.0.0 line.

Security Scope

EDEN security work includes, where applicable:

* Authentication and authorization
* Authority resolution and policy enforcement
* Solana transaction construction and verification
* Ed25519 signing boundaries
* Token-2022 integration
* Cryptographic commitment handling
* Quantum-readiness and migration controls
* Key-registration and ownership-verification flows
* Replay and cross-account protection
* API authentication and authorization
* Secret handling and sensitive-data logging
* Backend and worker execution paths
* Supply-chain and dependency security

The quantum-ready authority layer is designed to fail closed. Experimental or unsupported post-quantum signing mechanisms must not be treated as valid Solana transaction authorities.

Reporting a Vulnerability

Please report suspected security vulnerabilities privately rather than opening a public GitHub issue.

Use the repository’s private security reporting mechanism:

EdenLayerAI/local-ai Security Advisories

If private reporting is unavailable, contact the EDEN maintainers through the repository’s GitHub organization and request a private security contact.

Please Include

Where possible, provide:

* A concise description of the vulnerability
* Affected component, package, API, or workflow
* Affected version or commit
* Reproduction steps or proof of concept
* Expected behavior
* Actual behavior
* Security impact
* Any relevant logs, traces, or transaction identifiers
* Suggested mitigation, if known

Please do not include private keys, seed phrases, recovery secrets, authentication tokens, API keys, or other credentials in a report.

Initial Response

Maintainers will acknowledge a valid security report as soon as reasonably practicable.

The investigation may include:

1. Reproducing and validating the report
2. Determining affected components and attack surface
3. Assessing severity and exploitability
4. Identifying affected releases or deployments
5. Developing and testing a mitigation
6. Coordinating disclosure where appropriate

Response timing can vary according to severity, reproducibility, operational impact, and complexity.

Accepted Vulnerabilities

When a vulnerability is accepted:

* The affected code path will be investigated and contained.
* A security fix or mitigation will be developed where practical.
* Relevant tests will be added to prevent regression.
* Security-sensitive changes will be reviewed before release.
* Release notes or a security advisory may be published when appropriate.
* The reporter may be credited if they explicitly request attribution and disclosure is appropriate.

For critical vulnerabilities, maintainers may temporarily disable or restrict the affected capability rather than leaving an unsafe path operational.

Declined Reports

A report may be declined when it:

* Is not reproducible
* Does not present a meaningful security impact
* Describes intended behavior
* Requires compromised credentials or infrastructure outside EDEN’s control
* Relies exclusively on unsupported or intentionally disabled functionality
* Concerns an already disclosed vulnerability
* Is primarily a product or usability issue rather than a security issue

When practical, maintainers will explain why a report was declined.

Responsible Disclosure

Please allow maintainers reasonable time to investigate and mitigate a vulnerability before publicly disclosing technical exploitation details.

Do not use vulnerabilities to:

* Access data belonging to other users
* Exfiltrate credentials or private keys
* Destroy or alter production data
* Disrupt production services
* Perform denial-of-service attacks
* Manipulate financial assets or transactions
* Move funds without authorization

Good-faith security research should minimize impact and stop once sufficient evidence has been obtained.

Cryptographic and Quantum-Readiness Policy

EDEN’s current Solana authority model remains compatible with the cryptographic primitives actually supported by the Solana runtime.

Quantum-ready functionality is migration infrastructure, not a claim that Solana currently accepts post-quantum transaction signatures.

In particular:

* Ed25519 remains the current Solana transaction-signature boundary.
* Post-quantum algorithms are not enabled as native Solana authorities unless protocol support exists.
* Experimental algorithms must remain explicitly gated.
* PQ private keys must be generated independently rather than derived from an Ed25519 private seed unless a future protocol specification explicitly requires otherwise.
* Authority migration must be fail-closed.
* Cryptographic commitments must not expose their secret preimages.
* Secrets must never be written to logs, telemetry, API responses, or persistent authority records.
* Migration records must provide replay, epoch, account, and target-key binding.
* A commitment alone does not constitute proof of authority ownership.
* Unsupported cryptographic schemes must be rejected rather than silently downgraded.

Token and Financial Security

The canonical EDEN Token-2022 configuration must not be changed as a side effect of security or quantum-readiness work.

Security-sensitive transaction paths must validate:

* Network/cluster
* Program identity
* Mint identity
* Authority identity
* Transaction intent
* Account ownership
* Expected revisions
* Replay protection
* Policy authorization
* Final transaction state

Financial or blockchain actions should fail closed when required verification cannot be completed.

Secret Handling

EDEN maintainers will not request private keys, seed phrases, wallet recovery phrases, or other authentication secrets through GitHub issues, pull requests, or security reports.

If sensitive information is accidentally disclosed, do not publish additional copies. Treat the credential as compromised and rotate or revoke it through the appropriate authority.

Security Updates

Security fixes may be released independently of feature development.

Public product versioning remains 1.0.0. Internal security revisions, schema revisions, migration epochs, and policy revisions may change without changing the public product version.

Acknowledgements

EDEN may acknowledge responsible security researchers in security advisories or release documentation when:

* the report materially contributed to improving EDEN security,
* disclosure is appropriate,
* and the reporter agrees to attribution.

Anonymous disclosure is also supported.
