# Log4Shell (CVE-2021-44228) Security Notes

## Overview
Log4Shell is a critical remote code execution vulnerability in Apache Log4j 2's JNDI lookup feature. An attacker who can control log messages or log message parameters can execute arbitrary code loaded from LDAP and other JNDI-related endpoints. Only the `log4j-core` JAR is impacted; applications using only `log4j-api` without `log4j-core` are not affected.

## CVE Identifier
- **CVE-2021-44228**

## Severity
- **CVSS 3.1 Base Score: 10.0 — CRITICAL**
- Vector: `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H`
- Listed in CISA's Known Exploited Vulnerabilities Catalog.

## Affected Versions
- Apache Log4j2 versions `2.0-beta9` through `2.15.0` (excluding security releases 2.12.2, 2.12.3, and 2.3.1)
- Affected range per Apache: `[2.0-beta9, 2.3.1) ∪ [2.4, 2.12.2) ∪ [2.13.0, 2.15.0)`
- Only `log4j-core` is impacted.

## Fixed Version
- Java 6: **2.3.1**
- Java 7: **2.12.2**
- Java 8 and later: **2.15.0**
- Recommended target: **2.17.1+** (also fixes CVE-2021-45046, CVE-2021-45105, CVE-2021-44832)

## Remediation Actions
1. **Upgrade path** — Upgrade to a fixed version matching your Java runtime (see issue #2).
2. **Detecting vulnerable deployments** — Scan for `log4j-core` JARs in versions 2.0-beta9–2.15.0; use automated scanners (see issue #3).
3. **Hardening** — Disable JNDI lookups via `log4j2.formatMsgNoLookups=true` (Log4j >= 2.10) or remove `JndiLookup.class` from the JAR and restart the JVM (see issue #4).
4. **Automated dependency scanning** — Integrate SCA tools (Dependabot, Snyk, OWASP Dependency-Check) into CI (see issue #5).

## Sources
- Apache Logging Services Security Page: https://logging.apache.org/security.html
- NVD CVE-2021-44228: https://nvd.nist.gov/vuln/detail/cve-2021-44228
- Apache Log4j CVEs (ASF Blog): https://news.apache.org/foundation/entry/apache-log4j-cves
- Snyk Log4Shell remediation cheat sheet: https://snyk.io/blog/log4shell-remediation-cheat-sheet/
- Lunasec Log4Shell mitigation guide: https://www.lunasec.io/docs/blog/log4j-zero-day-mitigation-guide/
