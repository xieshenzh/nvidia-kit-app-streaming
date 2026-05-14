# Deployment Policy Check: isaac-lab

**Total: 37** | Critical: 0 | High: 5 | Medium: 7 | Low: 25

# Deployment Policy Check: isaac-lab: `client` (namespace: `isaac-lab-streaming`)

**Total: 9** | Critical: 0 | High: 0 | Medium: 3 | Low: 6

## Container using read-write root filesystem

- **Severity:** MEDIUM
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with containers with read-write root filesystem
- **Remediation:** Use a read-only root filesystem, and use volume mounts to allow writes to specific sub-directories depending on your application's needs.

**Violations:**

- Container 'nginx' uses a read-write root filesystem

## Container with privilege escalation allowed

- **Severity:** MEDIUM
- **Breaks Build/Deploy:** No
- **Description:** Alerts if a deployment has containers with allowPrivilegeEscalation set to true in its security context.
- **Remediation:** Verify that privileged escalation is required and cannot be provided with a subset of other controls. Disable privilege escalation by setting allowPrivilegeEscalation to false.

**Violations:**

- Container 'nginx' allows privilege escalation

## Pod Service Account Token Automatically Mounted

- **Severity:** MEDIUM
- **Breaks Build/Deploy:** No
- **Description:** Protect pod default service account tokens from compromise by minimizing the mounting of the default service account token to only those pods whose application requires interaction with the Kubernetes API.
- **Remediation:** Add `automountServiceAccountToken: false` or a value distinct from 'default' for the `serviceAccountName` key to the deployment's Pod configuration.

**Violations:**

- Deployment mounts the service account tokens.
- Namespace has name 'isaac-lab-streaming'
- Service Account is set to 'default'

## Drop All Capabilities

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert when a deployment does not drop all capabilities.
- **Remediation:** Ensure that the deployment manifest has `drop: ALL` in the securityContext section of the container manifest.

**Violations:**

- Container 'nginx' does not drop expected capabilities (drops no capabilities)

## Red Hat Package Manager in Image

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with components of the Red Hat/Fedora/CentOS package management system.
- **Remediation:** Run `rpm -e --nodeps $(rpm -qa '*rpm*' '*dnf*' '*libsolv*' '*hawkey*' 'yum*')` in the image build for production containers.

**Violations:**

- Container 'nginx' includes component 'dnf' (version 4.14.0-31.el9)
- Container 'nginx' includes component 'rpm' (version 4.16.1.3-39.el9)
- Container 'nginx' includes component 'yum' (version 4.14.0-31.el9)

## Required Annotation: Email

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'email' annotation
- **Remediation:** Redeploy your service and set the 'email' annotation as your email or your team's email.

**Violations:**

- Required annotation not found (found annotations: <empty>)

## Required Annotation: Owner/Team

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'owner' or 'team' annotation
- **Remediation:** Redeploy your service and set the 'owner' or 'team' annotation to yourself or your team respectively per organizational standards.

**Violations:**

- Required annotation not found (found annotations: <empty>)

## Required Image Label

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with images missing the specified label.
- **Remediation:** Request that the maintainer add the required label to the image.

**Violations:**

- Required label not found (found labels: architecture=aarch64, build-date=2026-05-13T04:44:00Z, com.redhat.component=nginx-124-container and 24 more)

## Required Label: Owner/Team

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'owner' or 'team' label
- **Remediation:** Redeploy your service and set the 'owner' or 'team' label to yourself or your team respectively per organizational standards.

**Violations:**

- Required label not found (found labels: app.kubernetes.io/managed-by=Helm, app.kubernetes.io/name=client, app.kubernetes.io/part-of=isaac-sim-streaming and 1 more)

---

# Deployment Policy Check: isaac-lab: `coturn` (namespace: `isaac-lab-streaming`)

**Total: 12** | Critical: 0 | High: 3 | Medium: 2 | Low: 7

## Fixable CVSS >= 7

- **Severity:** HIGH
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with fixable vulnerabilities with a CVSS of at least 7
- **Remediation:** Use your package manager to update to a fixed version in future builds or speak with your security team to mitigate the vulnerabilities.

| CVE | CVSS | Severity | Component | Version | Fixed In |
|-----|------|----------|-----------|---------|----------|
| CVE-2025-69421 | 7.5 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.4-1~deb13u2 |
| CVE-2025-69421 | 7.5 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.4-1~deb13u2 |
| CVE-2025-69421 | 7.5 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.4-1~deb13u2 |
| CVE-2026-28387 | 8.1 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28387 | 8.1 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28387 | 8.1 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28388 | 7.5 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28388 | 7.5 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28388 | 7.5 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28389 | 7.5 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28389 | 7.5 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28389 | 7.5 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28390 | 7.5 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28390 | 7.5 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28390 | 7.5 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-3104 | 7.5 | Important | bind9-dnsutils (coturn) | 1:9.20.15-1~deb13u1 | 1:9.20.21-1~deb13u1 |
| CVE-2026-3104 | 7.5 | Important | bind9-host (coturn) | 1:9.20.15-1~deb13u1 | 1:9.20.21-1~deb13u1 |
| CVE-2026-3104 | 7.5 | Important | bind9-libs (coturn) | 1:9.20.15-1~deb13u1 | 1:9.20.21-1~deb13u1 |
| CVE-2026-31789 | 9.8 | Critical | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-31789 | 9.8 | Critical | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-31789 | 9.8 | Critical | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-32710 | 9.9 | Critical | libmariadb3 (coturn) | 1:11.8.3-0+deb13u1 | 1:11.8.6-0+deb13u1 |
| CVE-2026-32710 | 9.9 | Critical | mariadb-common (coturn) | 1:11.8.3-0+deb13u1 | 1:11.8.6-0+deb13u1 |

## Fixable Severity at least Important

- **Severity:** HIGH
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with fixable vulnerabilities with a Severity Rating at least Important
- **Remediation:** Use your package manager to update to a fixed version in future builds or speak with your security team to mitigate the vulnerabilities.

| CVE | CVSS | Severity | Component | Version | Fixed In |
|-----|------|----------|-----------|---------|----------|
| CVE-2025-69421 | 7.5 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.4-1~deb13u2 |
| CVE-2025-69421 | 7.5 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.4-1~deb13u2 |
| CVE-2025-69421 | 7.5 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.4-1~deb13u2 |
| CVE-2026-28387 | 8.1 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28387 | 8.1 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28387 | 8.1 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28388 | 7.5 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28388 | 7.5 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28388 | 7.5 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28389 | 7.5 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28389 | 7.5 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28389 | 7.5 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28390 | 7.5 | Important | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28390 | 7.5 | Important | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-28390 | 7.5 | Important | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-3104 | 7.5 | Important | bind9-dnsutils (coturn) | 1:9.20.15-1~deb13u1 | 1:9.20.21-1~deb13u1 |
| CVE-2026-3104 | 7.5 | Important | bind9-host (coturn) | 1:9.20.15-1~deb13u1 | 1:9.20.21-1~deb13u1 |
| CVE-2026-3104 | 7.5 | Important | bind9-libs (coturn) | 1:9.20.15-1~deb13u1 | 1:9.20.21-1~deb13u1 |
| CVE-2026-31789 | 9.8 | Critical | libssl3t64 (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-31789 | 9.8 | Critical | openssl (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-31789 | 9.8 | Critical | openssl-provider-legacy (coturn) | 3.5.4-1~deb13u1 | 3.5.5-1~deb13u2 |
| CVE-2026-32710 | 9.9 | Critical | libmariadb3 (coturn) | 1:11.8.3-0+deb13u1 | 1:11.8.6-0+deb13u1 |
| CVE-2026-32710 | 9.9 | Critical | mariadb-common (coturn) | 1:11.8.3-0+deb13u1 | 1:11.8.6-0+deb13u1 |

## Secret Mounted as Environment Variable

- **Severity:** HIGH
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with Kubernetes secret mounted as environment variable
- **Remediation:** Migrate your secrets from environment variables to your security team's secret management solution.

**Violations:**

- Environment variable 'TURN_PASSWORD' is present in container 'coturn' and references a Secret

## Container using read-write root filesystem

- **Severity:** MEDIUM
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with containers with read-write root filesystem
- **Remediation:** Use a read-only root filesystem, and use volume mounts to allow writes to specific sub-directories depending on your application's needs.

**Violations:**

- Container 'coturn' uses a read-write root filesystem

## Container with privilege escalation allowed

- **Severity:** MEDIUM
- **Breaks Build/Deploy:** No
- **Description:** Alerts if a deployment has containers with allowPrivilegeEscalation set to true in its security context.
- **Remediation:** Verify that privileged escalation is required and cannot be provided with a subset of other controls. Disable privilege escalation by setting allowPrivilegeEscalation to false.

**Violations:**

- Container 'coturn' allows privilege escalation

## 90-Day Image Age

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with images that haven't been updated in 90 days
- **Remediation:** Rebuild your image, push a new minor version (with a new immutable tag), and update your service to use it.

**Violations:**

- Container 'coturn' has image created at 2025-12-18 14:30:10 (UTC)

## Drop All Capabilities

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert when a deployment does not drop all capabilities.
- **Remediation:** Ensure that the deployment manifest has `drop: ALL` in the securityContext section of the container manifest.

**Violations:**

- Container 'coturn' does not drop expected capabilities (drops no capabilities)

## Required Annotation: Email

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'email' annotation
- **Remediation:** Redeploy your service and set the 'email' annotation as your email or your team's email.

**Violations:**

- Required annotation not found (found annotations: <empty>)

## Required Annotation: Owner/Team

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'owner' or 'team' annotation
- **Remediation:** Redeploy your service and set the 'owner' or 'team' annotation to yourself or your team respectively per organizational standards.

**Violations:**

- Required annotation not found (found annotations: <empty>)

## Required Image Label

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with images missing the specified label.
- **Remediation:** Request that the maintainer add the required label to the image.

**Violations:**

- Required label not found (found labels: org.opencontainers.image.revision=6a0b3a648a0c53efa4b99c5b7034e09fbf66ae52, org.opencontainers.image.source=https://github.com/coturn/coturn, org.opencontainers.image.version=4.7.0-r4)

## Required Label: Owner/Team

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'owner' or 'team' label
- **Remediation:** Redeploy your service and set the 'owner' or 'team' label to yourself or your team respectively per organizational standards.

**Violations:**

- Required label not found (found labels: app.kubernetes.io/managed-by=Helm, app.kubernetes.io/name=coturn, app.kubernetes.io/part-of=isaac-sim-streaming and 1 more)

## Ubuntu Package Manager in Image

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with components of the Debian/Ubuntu package management system in the image.
- **Remediation:** Run `dpkg -r --force-all apt apt-get && dpkg -r --force-all debconf dpkg` in the image build for production containers.

**Violations:**

- Container 'coturn' includes component 'apt' (version 3.0.3)
- Container 'coturn' includes component 'dpkg' (version 1.22.21)

---

# Deployment Policy Check: isaac-lab: `isaac-sim` (namespace: `isaac-lab-streaming`)

**Total: 16** | Critical: 0 | High: 2 | Medium: 2 | Low: 12

## Fixable CVSS >= 7

- **Severity:** HIGH
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with fixable vulnerabilities with a CVSS of at least 7
- **Remediation:** Use your package manager to update to a fixed version in future builds or speak with your security team to mitigate the vulnerabilities.

| CVE | CVSS | Severity | Component | Version | Fixed In |
|-----|------|----------|-----------|---------|----------|
| CVE-2025-27516 | 8.8 | Moderate | jinja2 (isaac-sim) | 3.1.5 | 3.1.6 |
| CVE-2025-32414 | 7.5 | Important | libxml2 (tls-proxy) | 2.13.4-r5 | 2.13.4-r6 |
| CVE-2025-32415 | 7.5 | Important | libxml2 (tls-proxy) | 2.13.4-r5 | 2.13.4-r6 |
| CVE-2025-62727 | 7.5 | Important | starlette (isaac-sim) | 0.48.0 | 0.49.1 |
| CVE-2025-69223 | 7.5 | Important | aiohttp (isaac-sim) | 3.12.14 | 3.13.3 |
| CVE-2025-69223 | 7.5 | Important | aiohttp (isaac-sim) | 3.13.2 | 3.13.3 |
| CVE-2025-69227 | 7.5 | Moderate | aiohttp (isaac-sim) | 3.12.14 | 3.13.3 |
| CVE-2025-69227 | 7.5 | Moderate | aiohttp (isaac-sim) | 3.13.2 | 3.13.3 |
| CVE-2025-69228 | 7.5 | Moderate | aiohttp (isaac-sim) | 3.12.14 | 3.13.3 |
| CVE-2025-69228 | 7.5 | Moderate | aiohttp (isaac-sim) | 3.13.2 | 3.13.3 |
| CVE-2025-69421 | 7.5 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.6-r0 |
| CVE-2025-69421 | 7.5 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.6-r0 |
| CVE-2026-22184 | 7.8 | Important | zlib (tls-proxy) | 1.3.1-r2 | 1.3.2-r0 |
| CVE-2026-22695 | 7.1 | Important | libpng (tls-proxy) | 1.6.47-r0 | 1.6.54-r0 |
| CVE-2026-22801 | 7.8 | Important | libpng (tls-proxy) | 1.6.47-r0 | 1.6.54-r0 |
| CVE-2026-25210 | 7.8 | Important | libexpat (tls-proxy) | 2.7.0-r0 | 2.7.4-r0 |
| CVE-2026-25646 | 8.1 | Important | libpng (tls-proxy) | 1.6.47-r0 | 1.6.55-r0 |
| CVE-2026-25990 | 7.5 | Important | pillow (isaac-sim) | 11.3.0 | 12.1.1 |
| CVE-2026-26209 | 7.5 | Important | cbor2 (isaac-sim) | 5.8.0 | 5.9.0 |
| CVE-2026-27489 | 7.5 | Important | onnx (isaac-sim) | 1.20.1 | 1.21.0 |
| CVE-2026-28387 | 8.1 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28387 | 8.1 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28387 | 8.1 | Low | libssl3t64 (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-28387 | 8.1 | Low | openssl (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-28388 | 7.5 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28388 | 7.5 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28388 | 7.5 | Low | libssl3t64 (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-28388 | 7.5 | Low | openssl (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-28389 | 7.5 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28389 | 7.5 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28389 | 7.5 | Low | libssl3t64 (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-28389 | 7.5 | Low | openssl (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-28390 | 7.5 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28390 | 7.5 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28390 | 7.5 | Low | libssl3t64 (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-28390 | 7.5 | Low | openssl (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-28500 | 8.6 | Important | onnx (isaac-sim) | 1.20.1 | 1.21.0 |
| CVE-2026-31789 | 9.8 | Critical | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-31789 | 9.8 | Critical | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-31789 | 9.8 | Low | libssl3t64 (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-31789 | 9.8 | Low | openssl (isaac-sim) | 3.0.13-0ubuntu3.7 | 0:3.0.13-0ubuntu3.9 |
| CVE-2026-32281 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.2 |
| CVE-2026-32283 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.2 |
| CVE-2026-32597 | 7.5 | Important | pyjwt (isaac-sim) | 2.10.1 | 2.12.0 |
| CVE-2026-33186 | 9.1 | Critical | google.golang.org/grpc (isaac-sim) | v1.79.2 | 1.79.3 |
| CVE-2026-33810 | 8.2 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.2 |
| CVE-2026-33811 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.3 |
| CVE-2026-33814 | 7.5 | Important | golang.org/x/net (isaac-sim) | v0.51.0 | 0.53.0 |
| CVE-2026-33814 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.3 |
| CVE-2026-34070 | 7.5 | Important | langchain-core (isaac-sim) | 1.2.18 | 1.2.22 |
| CVE-2026-34445 | 8.6 | Important | onnx (isaac-sim) | 1.20.1 | 1.21.0 |
| CVE-2026-34480 | 7.5 | Moderate | org.apache.logging.log4j:log4j-core (isaac-sim) | 2.17.1 | 2.25.4 |
| CVE-2026-34513 | 7.5 | Low | aiohttp (isaac-sim) | 3.12.14 | 3.13.4 |
| CVE-2026-34513 | 7.5 | Low | aiohttp (isaac-sim) | 3.13.2 | 3.13.4 |
| CVE-2026-34513 | 7.5 | Low | aiohttp (isaac-sim) | 3.13.3 | 3.13.4 |
| CVE-2026-34515 | 7.5 | Moderate | aiohttp (isaac-sim) | 3.12.14 | 3.13.4 |
| CVE-2026-34515 | 7.5 | Moderate | aiohttp (isaac-sim) | 3.13.2 | 3.13.4 |
| CVE-2026-34515 | 7.5 | Moderate | aiohttp (isaac-sim) | 3.13.3 | 3.13.4 |
| CVE-2026-34516 | 7.5 | Important | aiohttp (isaac-sim) | 3.12.14 | 3.13.4 |
| CVE-2026-34516 | 7.5 | Important | aiohttp (isaac-sim) | 3.13.2 | 3.13.4 |
| CVE-2026-34516 | 7.5 | Important | aiohttp (isaac-sim) | 3.13.3 | 3.13.4 |
| CVE-2026-34520 | 9.1 | Critical | aiohttp (isaac-sim) | 3.12.14 | 3.13.4 |
| CVE-2026-34520 | 9.1 | Critical | aiohttp (isaac-sim) | 3.13.2 | 3.13.4 |
| CVE-2026-34520 | 9.1 | Critical | aiohttp (isaac-sim) | 3.13.3 | 3.13.4 |
| CVE-2026-3731 | 7.5 | Moderate | libssh-4 (isaac-sim) | 0.10.6-2ubuntu0.3 | 0:0.10.6-2ubuntu0.4 |
| CVE-2026-39820 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.3 |
| CVE-2026-39836 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.3 |
| CVE-2026-39883 | 7 | Important | go.opentelemetry.io/otel/sdk (isaac-sim) | v1.42.0 | 1.43.0 |
| CVE-2026-39892 | 9.8 | Moderate | cryptography (isaac-sim) | 46.0.5 | 46.0.7 |
| CVE-2026-40192 | 7.5 | Important | pillow (isaac-sim) | 11.3.0 | 12.2.0 |
| CVE-2026-40192 | 7.5 | Important | pillow (isaac-sim) | 12.1.1 | 12.2.0 |
| CVE-2026-41066 | 7.5 | Important | lxml (isaac-sim) | 4.9.4 | 6.1.0 |
| CVE-2026-41066 | 7.5 | Important | lxml (isaac-sim) | 6.0.2 | 6.1.0 |
| CVE-2026-41602 | 7.5 | Important | github.com/apache/thrift (isaac-sim) | v0.22.0 | 0.23.0 |
| CVE-2026-42215 | 8.8 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.47 |
| CVE-2026-42284 | 8.1 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.47 |
| CVE-2026-42561 | 7.5 | Important | python-multipart (isaac-sim) | 0.0.22 | 0.0.27 |
| CVE-2026-44243 | 7.1 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.48 |
| CVE-2026-44244 | 7.8 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.49 |
| CVE-2026-44843 | 8.2 | Important | langchain-core (isaac-sim) | 1.2.18 | 1.3.3 |
| CVE-2026-45134 | 7.1 | Important | langchain-classic (isaac-sim) | 1.0.2 | 1.0.7 |
| CVE-2026-45134 | 7.1 | Important | langsmith (isaac-sim) | 0.7.16 | 0.6.0 |
| CVE-2026-45134 | 7.1 | Important | langsmith (isaac-sim) | 0.7.16 | 0.8.0 |
| CVE-2026-4878 | 7 | Moderate | libcap2 (isaac-sim) | 1:2.66-5ubuntu2.2 | 1:2.66-5ubuntu2.4 |
| CVE-2026-5773 | 7.5 | Low | curl (isaac-sim) | 8.5.0-2ubuntu10.8 | 0:8.5.0-2ubuntu10.9 |
| CVE-2026-5773 | 7.5 | Low | libcurl3t64-gnutls (isaac-sim) | 8.5.0-2ubuntu10.8 | 0:8.5.0-2ubuntu10.9 |
| CVE-2026-5773 | 7.5 | Low | libcurl4t64 (isaac-sim) | 8.5.0-2ubuntu10.8 | 0:8.5.0-2ubuntu10.9 |
| GHSA-mv93-w799-cj2w | 7 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.50 |
| GHSA-q56x-g2fj-4rj6 | 7.1 | Important | onnx (isaac-sim) | 1.20.1 | 1.21.0 |

## Fixable Severity at least Important

- **Severity:** HIGH
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with fixable vulnerabilities with a Severity Rating at least Important
- **Remediation:** Use your package manager to update to a fixed version in future builds or speak with your security team to mitigate the vulnerabilities.

| CVE | CVSS | Severity | Component | Version | Fixed In |
|-----|------|----------|-----------|---------|----------|
| CVE-2025-32414 | 7.5 | Important | libxml2 (tls-proxy) | 2.13.4-r5 | 2.13.4-r6 |
| CVE-2025-32415 | 7.5 | Important | libxml2 (tls-proxy) | 2.13.4-r5 | 2.13.4-r6 |
| CVE-2025-62727 | 7.5 | Important | starlette (isaac-sim) | 0.48.0 | 0.49.1 |
| CVE-2025-69223 | 7.5 | Important | aiohttp (isaac-sim) | 3.12.14 | 3.13.3 |
| CVE-2025-69223 | 7.5 | Important | aiohttp (isaac-sim) | 3.13.2 | 3.13.3 |
| CVE-2025-69421 | 7.5 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.6-r0 |
| CVE-2025-69421 | 7.5 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.6-r0 |
| CVE-2026-22184 | 7.8 | Important | zlib (tls-proxy) | 1.3.1-r2 | 1.3.2-r0 |
| CVE-2026-22695 | 7.1 | Important | libpng (tls-proxy) | 1.6.47-r0 | 1.6.54-r0 |
| CVE-2026-22801 | 7.8 | Important | libpng (tls-proxy) | 1.6.47-r0 | 1.6.54-r0 |
| CVE-2026-25210 | 7.8 | Important | libexpat (tls-proxy) | 2.7.0-r0 | 2.7.4-r0 |
| CVE-2026-25646 | 8.1 | Important | libpng (tls-proxy) | 1.6.47-r0 | 1.6.55-r0 |
| CVE-2026-25990 | 7.5 | Important | pillow (isaac-sim) | 11.3.0 | 12.1.1 |
| CVE-2026-26209 | 7.5 | Important | cbor2 (isaac-sim) | 5.8.0 | 5.9.0 |
| CVE-2026-27489 | 7.5 | Important | onnx (isaac-sim) | 1.20.1 | 1.21.0 |
| CVE-2026-28387 | 8.1 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28387 | 8.1 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28388 | 7.5 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28388 | 7.5 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28389 | 7.5 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28389 | 7.5 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28390 | 7.5 | Important | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28390 | 7.5 | Important | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-28500 | 8.6 | Important | onnx (isaac-sim) | 1.20.1 | 1.21.0 |
| CVE-2026-31789 | 9.8 | Critical | libcrypto3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-31789 | 9.8 | Critical | libssl3 (tls-proxy) | 3.3.3-r0 | 3.3.7-r0 |
| CVE-2026-32281 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.2 |
| CVE-2026-32283 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.2 |
| CVE-2026-32597 | 7.5 | Important | pyjwt (isaac-sim) | 2.10.1 | 2.12.0 |
| CVE-2026-33186 | 9.1 | Critical | google.golang.org/grpc (isaac-sim) | v1.79.2 | 1.79.3 |
| CVE-2026-33810 | 8.2 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.2 |
| CVE-2026-33811 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.3 |
| CVE-2026-33814 | 7.5 | Important | golang.org/x/net (isaac-sim) | v0.51.0 | 0.53.0 |
| CVE-2026-33814 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.3 |
| CVE-2026-34070 | 7.5 | Important | langchain-core (isaac-sim) | 1.2.18 | 1.2.22 |
| CVE-2026-34445 | 8.6 | Important | onnx (isaac-sim) | 1.20.1 | 1.21.0 |
| CVE-2026-34516 | 7.5 | Important | aiohttp (isaac-sim) | 3.12.14 | 3.13.4 |
| CVE-2026-34516 | 7.5 | Important | aiohttp (isaac-sim) | 3.13.2 | 3.13.4 |
| CVE-2026-34516 | 7.5 | Important | aiohttp (isaac-sim) | 3.13.3 | 3.13.4 |
| CVE-2026-34520 | 9.1 | Critical | aiohttp (isaac-sim) | 3.12.14 | 3.13.4 |
| CVE-2026-34520 | 9.1 | Critical | aiohttp (isaac-sim) | 3.13.2 | 3.13.4 |
| CVE-2026-34520 | 9.1 | Critical | aiohttp (isaac-sim) | 3.13.3 | 3.13.4 |
| CVE-2026-39820 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.3 |
| CVE-2026-39836 | 7.5 | Important | stdlib (isaac-sim) | 1.26.1 | 1.26.3 |
| CVE-2026-39883 | 7 | Important | go.opentelemetry.io/otel/sdk (isaac-sim) | v1.42.0 | 1.43.0 |
| CVE-2026-40192 | 7.5 | Important | pillow (isaac-sim) | 11.3.0 | 12.2.0 |
| CVE-2026-40192 | 7.5 | Important | pillow (isaac-sim) | 12.1.1 | 12.2.0 |
| CVE-2026-41066 | 7.5 | Important | lxml (isaac-sim) | 4.9.4 | 6.1.0 |
| CVE-2026-41066 | 7.5 | Important | lxml (isaac-sim) | 6.0.2 | 6.1.0 |
| CVE-2026-41486 | 0 | Important | ray (isaac-sim) | 2.52.1 | 2.55.0 |
| CVE-2026-41602 | 7.5 | Important | github.com/apache/thrift (isaac-sim) | v0.22.0 | 0.23.0 |
| CVE-2026-42215 | 8.8 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.47 |
| CVE-2026-42284 | 8.1 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.47 |
| CVE-2026-42311 | 0 | Important | pillow (isaac-sim) | 11.3.0 | 12.2.0 |
| CVE-2026-42311 | 0 | Important | pillow (isaac-sim) | 12.1.1 | 12.2.0 |
| CVE-2026-42561 | 7.5 | Important | python-multipart (isaac-sim) | 0.0.22 | 0.0.27 |
| CVE-2026-44243 | 7.1 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.48 |
| CVE-2026-44244 | 7.8 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.49 |
| CVE-2026-44431 | 0 | Important | urllib3 (isaac-sim) | 2.6.3 | 2.7.0 |
| CVE-2026-44432 | 0 | Important | urllib3 (isaac-sim) | 2.6.3 | 2.7.0 |
| CVE-2026-44843 | 8.2 | Important | langchain-core (isaac-sim) | 1.2.18 | 1.3.3 |
| CVE-2026-45022 | 0 | Important | github.com/go-git/go-git/v5 (isaac-sim) | v5.17.0 | 5.19.0 |
| CVE-2026-45134 | 7.1 | Important | langchain-classic (isaac-sim) | 1.0.2 | 1.0.7 |
| CVE-2026-45134 | 7.1 | Important | langsmith (isaac-sim) | 0.7.16 | 0.6.0 |
| CVE-2026-45134 | 7.1 | Important | langsmith (isaac-sim) | 0.7.16 | 0.8.0 |
| GHSA-mv93-w799-cj2w | 7 | Important | gitpython (isaac-sim) | 3.1.46 | 3.1.50 |
| GHSA-q56x-g2fj-4rj6 | 7.1 | Important | onnx (isaac-sim) | 1.20.1 | 1.21.0 |

## Container using read-write root filesystem

- **Severity:** MEDIUM
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with containers with read-write root filesystem
- **Remediation:** Use a read-only root filesystem, and use volume mounts to allow writes to specific sub-directories depending on your application's needs.

**Violations:**

- Container 'isaac-sim' uses a read-write root filesystem
- Container 'tls-proxy' uses a read-write root filesystem

## Container with privilege escalation allowed

- **Severity:** MEDIUM
- **Breaks Build/Deploy:** No
- **Description:** Alerts if a deployment has containers with allowPrivilegeEscalation set to true in its security context.
- **Remediation:** Verify that privileged escalation is required and cannot be provided with a subset of other controls. Disable privilege escalation by setting allowPrivilegeEscalation to false.

**Violations:**

- Container 'isaac-sim' allows privilege escalation
- Container 'tls-proxy' allows privilege escalation

## 90-Day Image Age

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with images that haven't been updated in 90 days
- **Remediation:** Rebuild your image, push a new minor version (with a new immutable tag), and update your service to use it.

**Violations:**

- Container 'tls-proxy' has image created at 2025-04-16 14:50:31 (UTC)

## ADD Command used instead of COPY

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments using an ADD command
- **Remediation:** Replace ADD with COPY when adding new files to the image. Per https://docs.docker.com/develop/develop-images/dockerfile_best-practices, it is better to use RUN curl instead of ADD if you need to access a URL.

**Violations:**

- Dockerfile line 'ADD alpine-minirootfs-3.21.3-x86_64....' found in container 'tls-proxy'
- Dockerfile line 'ADD file:ddf1aa62235de6657123492b19d...' found in container 'isaac-sim'

## Alpine Linux Package Manager (apk) in Image

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with the Alpine Linux package manager (apk) present
- **Remediation:** Run `apk --purge del apk-tools` in the image build for production containers.

**Violations:**

- Container 'tls-proxy' includes component 'apk-tools' (version 2.14.6-r3)

## Curl in Image

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with curl present
- **Remediation:** Use your package manager's "remove", "purge" or "erase" command to remove curl from the image build for production containers. Ensure that any configuration files are also removed.

**Violations:**

- Container 'isaac-sim' includes component 'curl' (version 8.5.0-2ubuntu10.8)
- Container 'tls-proxy' includes component 'curl' (version 8.12.1-r1)

## Docker CIS 4.1: Ensure That a User for the Container Has Been Created

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Containers should run as a non-root user
- **Remediation:** Ensure that the Dockerfile for each container switches from the root user

**Violations:**

- Container 'isaac-sim' has image with user 'root'
- Container 'tls-proxy' has image with user 'root'

## Drop All Capabilities

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert when a deployment does not drop all capabilities.
- **Remediation:** Ensure that the deployment manifest has `drop: ALL` in the securityContext section of the container manifest.

**Violations:**

- Container 'isaac-sim' does not drop expected capabilities (drops no capabilities)
- Container 'tls-proxy' does not drop expected capabilities (drops no capabilities)

## Required Annotation: Email

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'email' annotation
- **Remediation:** Redeploy your service and set the 'email' annotation as your email or your team's email.

**Violations:**

- Required annotation not found (found annotations: <empty>)

## Required Annotation: Owner/Team

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'owner' or 'team' annotation
- **Remediation:** Redeploy your service and set the 'owner' or 'team' annotation to yourself or your team respectively per organizational standards.

**Violations:**

- Required annotation not found (found annotations: <empty>)

## Required Image Label

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with images missing the specified label.
- **Remediation:** Request that the maintainer add the required label to the image.

**Violations:**

- Required label not found (found labels: description=Dockerfile for building and running the Isaac Lab framework insi, org.opencontainers.image.ref.name=ubuntu, org.opencontainers.image.version=24.04 and 1 more)
- Required label not found (found labels: maintainer=NGINX Docker Maintainers <docker-maint@nginx.com>)

## Required Label: Owner/Team

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments missing the 'owner' or 'team' label
- **Remediation:** Redeploy your service and set the 'owner' or 'team' label to yourself or your team respectively per organizational standards.

**Violations:**

- Required label not found (found labels: app.kubernetes.io/managed-by=Helm, app.kubernetes.io/name=isaac-sim, app.kubernetes.io/part-of=isaac-sim-streaming and 1 more)

## Ubuntu Package Manager in Image

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with components of the Debian/Ubuntu package management system in the image.
- **Remediation:** Run `dpkg -r --force-all apt apt-get && dpkg -r --force-all debconf dpkg` in the image build for production containers.

**Violations:**

- Container 'isaac-sim' includes component 'apt' (version 2.8.3)
- Container 'isaac-sim' includes component 'dpkg' (version 1.22.6ubuntu6.5)

## Wget in Image

- **Severity:** LOW
- **Breaks Build/Deploy:** No
- **Description:** Alert on deployments with wget present
- **Remediation:** Use your package manager's "remove" command to remove wget from the image build for production containers.

**Violations:**

- Container 'isaac-sim' includes component 'wget' (version 1.21.4-1ubuntu4.1)

---

