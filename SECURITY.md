# Security Policy

## Supported Versions

Only the latest version on `main` is supported with security updates.

## Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly.

**Email**: security@altresear.ch

Please include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

## Response Timeline

- **48 hours**: Acknowledgment of your report
- **1 week**: Initial assessment and severity classification
- **30 days**: Fix deployed (for confirmed vulnerabilities)

## Scope

### In Scope

- Skill definitions that could enable unintended code execution
- API key or credential exposure in skill references
- Prompt injection vectors in skill templates
- Trust label miscalculation logic
- Untrusted data handling in agent metadata rendering

### Out of Scope

- Vulnerabilities in third-party dependencies (report to upstream)
- Issues requiring physical access to the machine
- Social engineering attacks
- The ERC-8004 smart contracts themselves (report to the contracts repo)
- The 8004scan API (report to the 8004scan team)

## Responsible Disclosure

- Do not publicly disclose the vulnerability before a fix is available
- Do not exploit the vulnerability beyond what is necessary to demonstrate it
- Do not access or modify other users' data

## Our Commitment

- We will acknowledge your report promptly
- We will keep you informed of progress
- We will credit you in the fix (unless you prefer anonymity)
- We will not take legal action against good-faith security researchers
