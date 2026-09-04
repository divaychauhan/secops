# 🔐 DevSecOps

## What is DevSecOps?

**DevSecOps** means integrating security practices and controls throughout the **Software Development Life Cycle (SDLC)** instead of treating security as a final manual stage.

The main goal of DevSecOps is to:

* Detect security vulnerabilities early
* Automate security checks
* Enforce security policies in CI/CD pipelines
* Secure application code, dependencies, infrastructure, and containers
* Continuously monitor applications and infrastructure in production
* Make security a **shared responsibility** across Development, Security, and Operations teams

---

# 🚀 What Does DevSecOps Do?

DevSecOps integrates security into every stage of the software delivery lifecycle.

### 1. Integrates Security into Development

Security is introduced from the beginning of the development process rather than after the application is completed.

### 2. SAST — Static Application Security Testing

Analyzes source code without executing the application.

**Examples:**

* SonarQube
* Checkmarx

### 3. SCA — Software Composition Analysis

Scans third-party dependencies and open-source libraries for known vulnerabilities and licensing issues.

**Examples:**

* Snyk
* OWASP Dependency-Check

### 4. Secret Scanning

Detects accidentally exposed secrets such as:

* API keys
* Passwords
* Access tokens
* Private keys
* Cloud credentials

**Examples:**

* Gitleaks
* GitGuardian

### 5. Infrastructure as Code Security

Scans Terraform, Kubernetes manifests, CloudFormation, and other IaC configurations for security misconfigurations.

**Examples:**

* Checkov
* Trivy

### 6. Container Image Scanning

Scans Docker/container images for vulnerabilities in:

* OS packages
* Application dependencies
* Libraries
* Configuration

**Examples:**

* Trivy
* Grype

### 7. DAST — Dynamic Application Security Testing

Tests a running application from the outside to identify runtime security vulnerabilities.

**Examples:**

* OWASP ZAP
* Burp Suite

### 8. Automates Security Checks in CI/CD

Security tools are integrated directly into CI/CD pipelines.

**Examples:**

* GitHub Actions
* GitLab CI/CD
* Jenkins

### 9. Enforces Security Gates

Security gates prevent vulnerable code or infrastructure from progressing to the next deployment stage.

For example:

```text
Developer
    ↓
Git Push
    ↓
SAST
    ↓
SCA
    ↓
Secret Scan
    ↓
IaC Scan
    ↓
Container Scan
    ↓
Security Gate
    ↓
Build
    ↓
Deploy
```

### 10. Production Security Monitoring

Continuously monitors applications, containers, hosts, and infrastructure for suspicious behavior.

**Example:**

* Falco

### 11. Vulnerability Management

Identifies, prioritizes, tracks, and remediates security vulnerabilities.

**Examples:**

* Snyk
* Trivy
* OWASP Dependency-Check

### 12. Security as a Shared Responsibility

DevSecOps makes security a shared responsibility between:

```text
Development + Security + Operations
```

Security is not owned only by the security team.

### 13. Code Quality Checks

Checks code for:

* Bugs
* Vulnerabilities
* Maintainability issues
* Reliability problems

**Example:**

* SonarQube

### 14. Code Smell Detection

Identifies code patterns that may indicate poor maintainability or design problems.

**Example:**

* SonarQube

### 15. CI/CD Security Scanning

Security checks are automatically executed during CI/CD pipelines to prevent insecure code and configurations from reaching production.

---

# 🛠️ DevSecOps Tools & Technologies

| Security Area            | Tools                                 |
| ------------------------ | ------------------------------------- |
| Secure Code / SAST       | SonarQube, Checkmarx                  |
| Dependency / SCA         | Snyk, OWASP Dependency-Check          |
| Secret Detection         | Gitleaks, GitGuardian                 |
| IaC Security             | Trivy, Checkov                        |
| Container Image Scanning | Trivy, Grype                          |
| DAST                     | OWASP ZAP, Burp Suite                 |
| CI/CD Automation         | GitHub Actions, GitLab CI/CD, Jenkins |
| Security Gates           | SonarQube Quality Gates, OPA          |
| Runtime Security         | Falco                                 |
| Vulnerability Management | Snyk, Trivy                           |

---

# 🔄 DevSecOps CI/CD Security Pipeline

A typical DevSecOps pipeline can look like this:

```text
                  ┌──────────────────┐
                  │     Developer    │
                  └────────┬─────────┘
                           │
                           ▼
                    ┌─────────────┐
                    │ Git Push/PR │
                    └──────┬──────┘
                           │
             ┌─────────────┴─────────────┐
             ▼                           ▼
       ┌───────────┐               ┌───────────┐
       │    SAST   │               │   Secret  │
       │ SonarQube │               │  Gitleaks │
       └─────┬─────┘               └─────┬─────┘
             │                           │
             └─────────────┬─────────────┘
                           ▼
                    ┌─────────────┐
                    │     SCA     │
                    │ Snyk / OWASP│
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────┐
                    │  IaC Scan   │
                    │Checkov/Trivy│
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────┐
                    │   Docker    │
                    │Image Scan   │
                    │Trivy/Grype  │
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────┐
                    │Security Gate│
                    │ OPA / Sonar │
                    └──────┬──────┘
                           │
                    ┌──────┴──────┐
                    │             │
                  PASS           FAIL
                    │             │
                    ▼             ▼
                 Deploy        Block
                    │
                    ▼
             ┌──────────────┐
             │   DAST Scan  │
             │ OWASP ZAP    │
             └──────┬───────┘
                    │
                    ▼
             ┌──────────────┐
             │  Production  │
             └──────┬───────┘
                    │
                    ▼
             ┌──────────────┐
             │   Runtime    │
             │   Security   │
             │    Falco     │
             └──────────────┘
```

---

# 🧠 Core DevSecOps Concepts

## 1. Shift Left Security

**Shift Left** means moving security testing earlier in the SDLC.

Instead of finding vulnerabilities in production:

```text
Traditional:

Development → Build → Deploy → Production → Security Testing
```

DevSecOps:

```text
Development → Security Testing → Build → Deploy → Production
```

### Goal

Find and fix vulnerabilities as early as possible because fixing security issues early is generally faster and cheaper.

---

# 2. Shift Right Security

**Shift Right** means continuing security practices after deployment and during production.

Examples:

* Runtime monitoring
* Vulnerability monitoring
* DAST
* Threat detection
* Incident response
* Runtime security

Example:

```text
Build → Deploy → Production → Monitor → Detect → Respond
```

---

# 3. Defense in Depth

**Defense in Depth** means using multiple layers of security instead of relying on a single security control.

Example:

```text
WAF
 ↓
Load Balancer
 ↓
Network Security
 ↓
IAM
 ↓
Container Security
 ↓
Application Security
 ↓
Database Security
```

If one security layer fails, other layers can still provide protection.

---

# 4. Least Privilege

Users, applications, services, and workloads should receive only the permissions they actually need.

Example:

Instead of giving an application:

```text
AdministratorAccess
```

give it only the required permissions:

```text
Read access to S3 bucket
```

---

# 5. Zero Trust

**Zero Trust** follows the principle:

> Never trust by default. Always verify.

Access should be based on:

* Identity
* Authentication
* Authorization
* Device/security context
* Network context
* Required permissions

---

# 6. Risk Management

Risk management involves:

```text
Identify → Assess → Prioritize → Mitigate → Monitor
```

Not every vulnerability has the same level of risk.

Teams should prioritize vulnerabilities based on factors such as:

* Severity
* Exploitability
* Business impact
* Exposure
* Availability of a fix

---

# 7. Security Gates

Security gates prevent insecure code or infrastructure from progressing through the pipeline.

Example:

```text
SAST
  ↓
SCA
  ↓
Secret Scan
  ↓
Container Scan
  ↓
Security Gate
  ↓
Deploy
```

Example policy:

```text
Critical vulnerabilities = 0
High vulnerabilities = 0
Secret detected = FAIL
```

If the policy is violated:

```text
Pipeline → FAILED
Deployment → BLOCKED
```

---

# 8. Threat Modeling

Threat modeling identifies potential security threats before they become vulnerabilities.

A common approach is **STRIDE**:

```text
S → Spoofing
T → Tampering
R → Repudiation
I → Information Disclosure
D → Denial of Service
E → Elevation of Privilege
```

Example:

For a web application, ask:

* Who can access the application?
* Can an attacker modify requests?
* Can sensitive information leak?
* Can an attacker gain higher privileges?
* Can the application be taken down?

---

# 9. Attack Surface

The **attack surface** represents all possible entry points an attacker could use to compromise a system.

Examples:

* APIs
* Web applications
* Open ports
* Cloud services
* Containers
* Dependencies
* Credentials
* Public S3 buckets
* Exposed infrastructure

The goal is to reduce unnecessary attack surfaces.

---

# 10. CIA Triad

The CIA Triad represents three fundamental security principles.

### Confidentiality

Only authorized users should access information.

Example:

```text
Database credentials should not be publicly accessible.
```

### Integrity

Data should not be modified without authorization.

Example:

```text
An attacker should not be able to modify transaction records.
```

### Availability

Systems and data should remain available when required.

Example:

```text
Application should remain available during normal and unexpected traffic.
```

```text
              CIA TRIAD

          Confidentiality
                 /\
                /  \
               /    \
              /      \
             /        \
        Integrity ---- Availability
```

---

# 🔐 DevSecOps Security Layers

```text
                    DevSecOps
                        │
       ┌────────────────┼────────────────┐
       │                │                │
       ▼                ▼                ▼
   Application        Pipeline       Infrastructure
       │                │                │
       ▼                ▼                ▼
     SAST          CI/CD Security      IaC Scan
     SCA           Security Gates      Cloud Security
     DAST          Secret Scan         Container Scan
       │                │                │
       └────────────────┼────────────────┘
                        ▼
                Runtime Security
                        │
                        ▼
                    Monitoring
                        │
                        ▼
                 Vulnerability
                   Management
```

---

# 🎯 Main Goal of DevSecOps

The ultimate goal of DevSecOps is:

```text
Build Secure
      ↓
Test Secure
      ↓
Deploy Secure
      ↓
Run Secure
      ↓
Monitor Continuously
      ↓
Improve Continuously
```

DevSecOps helps organizations deliver software **faster and more securely** by integrating automated security practices throughout the entire SDLC.
