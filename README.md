# Awesome-QA-Identity-Access-Management-IAM

# Awesome QA Identity & Access Management (IAM)

> A curated list of top Identity and Access Management (IAM) platforms for QA teams — both SaaS/Hosted commercial identity providers and open-source alternatives for enforcing SSO, SCIM provisioning, and role-based access across testing infrastructure.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [BrowserStack IAM](#browserstack-iam)
  - [Okta](#okta)
  - [Microsoft Entra ID](#microsoft-entra-id)
  - [OneLogin](#onelogin)
  - [Ping Identity (ForgeRock)](#ping-identity-forgerock)
  - [CyberArk Identity](#cyberark-identity)
  - [JumpCloud](#jumpcloud)
  - [Auth0](#auth0)
- [Open-Source Software](#-open-source-software)
  - [Keycloak](#keycloak)
  - [Casdoor](#casdoor)
  - [Authentik](#authentik)
  - [Zitadel](#zitadel)
  - [Apache Syncope](#apache-syncope)
  - [Evolveum midPoint](#evolveum-midpoint)
  - [Shibboleth](#shibboleth)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Identity and Access Management platforms. These are not open-source but are included as reference points for feature comparison.

### BrowserStack IAM
**Type:** QA-native IAM with SSO, SCIM, and granular RBAC
BrowserStack's IAM is purpose-built for QA organizations, with **Single Sign-On (SSO)** supporting SAML 2.0 (Okta, Azure AD, OneLogin, ADFS, Open SAML) and Google OAuth . **Auto User Provisioning** via SCIM 2.0 automatically syncs users and de-provisions them from your identity provider, with attribute assignment for IAM roles, product access, and team membership . The **RBAC model** is split into IAM roles (Owner, Admin, User) governing administrative access and product roles providing granular access within specific products like Test Management and Test Reporting [citation:4]. Teams can be created to mirror organizational structure, with team-level Admin or User roles [citation:4]. An Open SCIM connector supports any IdP that implements the SCIM standard .
**Best for:** QA organizations wanting native SSO and SCIM integration with granular product-level role control, without building custom identity infrastructure.

### Okta
**Type:** Enterprise IAM with standard and custom admin roles
Okta provides standard admin roles (Super Admin, Org Admin, App Admin, Group Admin, Read-Only Admin) with predefined permissions, plus custom roles that bundle granular permissions. Role assignments can be scoped to specific resources for least-privilege access. It is the most widely adopted vendor-neutral IdP, with a vast integration catalogue for QA tools.

### Microsoft Entra ID
**Type:** Identity platform with built-in and custom roles
Entra ID provides built-in roles and custom roles assignable at Tenant, Administrative Unit, or specific resource scope (groups, enterprise apps, app registrations). PIM enables just-in-time role activation with approval workflows. For QA, this allows testers to be granted access only to specific app registrations or groups relevant to their testing scope.

### OneLogin
**Type:** IAM with app-centric roles and attribute mappings
OneLogin roles are collections of apps; assigning a user to a role grants access to all apps in that role. Mappings can automatically assign users to roles based on directory attributes (e.g., Department = QA). BrowserStack provides a native OneLogin SSO connector with SAML 2.0 support .

### Ping Identity (ForgeRock)
**Type:** AI-forward IAM with fraud and risk protection
Ping Identity (now merged with ForgeRock) provides modern, modular, cloud-ready IAM for multi-cloud and hybrid environments, with AI/ML-driven access decisions based on behavior. It covers customer and workforce identity management, identity verification, fine-grained authorization, and IGA. Pricing starts at $35K/year for PingOne for Customers and $3/user/month (5,000-user minimum) for Workforce [citation:3].

### CyberArk Identity
**Type:** Identity administration with role-based rights and dynamic membership
CyberArk Identity uses roles as the unit of access control, with **dynamic roles** automatically adding members based on attribute logic (e.g., all users from a specified country) written in JavaScript. Administrative rights control specific functionality like creating roles and managing users.

### JumpCloud
**Type:** Cloud directory with custom admin roles
JumpCloud supports custom admin roles built from permission categories including Access Management, Application Management, Core Administration, and Device Management, with granular sub-permissions. A maximum of 20 custom roles is supported.

### Auth0
**Type:** Developer IAM with API-level RBAC
Auth0 enables RBAC for APIs through Dashboard or Management API, controlling the intersection of requested and assigned permissions in the access token's `scope` claim. This allows QA teams to build custom tooling where API access is gated by role.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Identity and Access Management tools. The open-source ecosystem spans **full IAM platforms with SSO and SCIM**, **modern AI-native identity servers**, and **identity governance systems**.

### Keycloak
**Stack:** Java (Quarkus) | **License:** Apache-2.0
Keycloak is the most widely deployed open-source IAM platform, providing realm-level roles, client roles, composite roles, and group-based role mapping. It supports OAuth 2.0/OIDC, SAML 2.0, LDAP/AD user federation, and **SCIM 2.0 server** for receiving users from Entra ID or Okta (since version 26.8) [citation:6]. Fine-grained authorization services allow defining resources, scopes, and policies for complex access decisions. It has the most extension points for Java developers [citation:6].
**Best for:** QA organizations wanting a proven, full-featured IAM foundation with SSO, LDAP integration, and SCIM support for test infrastructure access management.

### Casdoor
**Stack:** Go / React | **License:** Apache-2.0
Casdoor is an AI-native IAM/SSO platform with a built-in **MCP server and OAuth 2.1 for MCP**, making it unique among open-source IAM tools [citation:6]. It supports OAuth 2.0/OIDC, SAML 2.0, CAS, LDAP, RADIUS, and **SCIM 2.0 server** for receiving users from Entra ID or Okta [citation:6]. The login page is configuration-driven per application, with webhooks and REST API for custom logic. It has 70+ built-in social and enterprise providers including WeChat, DingTalk, Lark, and Alipay [citation:6].
**Best for:** QA teams wanting a modern, Go-based IAM with MCP support and broad protocol coverage, particularly those integrating AI agents into their workflows.

### Authentik
**Stack:** Python / Go | **License:** MIT core / Commercial enterprise
Authentik provides the **most flexible sign-in flow engine** among open-source IAM tools, with flows and stages edited in the admin interface and Python expression policies for custom logic [citation:6]. It supports OAuth 2.0/OIDC, SAML 2.0, LDAP outpost, RADIUS outpost, and **SCIM source** for syncing users from external directories [citation:6]. It also includes a proxy provider for Traefik, Caddy, Nginx, and Envoy.
**Best for:** QA teams needing highly customizable authentication flows with proxy-based access control, accepting the Python/Go stack requirements.

### Zitadel
**Stack:** Go / TypeScript | **License:** AGPL-3.0
Zitadel is a cloud-native identity platform with a focus on multi-tenancy and self-service. It provides OIDC, SAML, MFA, passwordless, and user management with a modern API-first design. It supports **SCIM 2.0 server** (users, preview) and LDAP identity provider [citation:6].
**Best for:** Teams wanting a cloud-native, multi-tenant identity platform with modern APIs, accepting AGPL licensing.

### Apache Syncope
**Stack:** Java | **License:** Apache-2.0
Apache Syncope is an open-source IAM and IGA platform for managing digital identities, provisioning, authentication, and access control. It supports user/group/role management, automated provisioning workflows, RBAC, delegated administration, LDAP/AD/database connectors, SAML 2.0, OIDC, and SCIM [citation:12].
**Best for:** Organizations seeking a standards-based, Apache-governed IGA platform with strong connector support.

### Evolveum midPoint
**Stack:** Java | **License:** Open Source (subscription model)
Evolveum midPoint is a comprehensive open-source IGA platform with automated provisioning/deprovisioning, policy-based approvals, segregation of duties controls, access certification campaigns, and role mining. Subscription-based with no license fees. It is noted as an open-source identity governance system for synchronization, roles, provisioning, and access requests [citation:12].
**Best for:** Organizations needing full IGA with lifecycle automation and governance controls without per-identity licensing costs.

### Shibboleth
**Stack:** Java | **License:** Open Source (Shibboleth Consortium)
Shibboleth offers web-based single sign-on (SSO) and federated identity solutions, particularly recommended for higher education and research institutions. It enables organizations to expand user authentication systems, granting access to online resources from associated organizations, with centralized auditing and reporting for authentication events [citation:3].
**Best for:** Higher education and research QA teams needing federated identity across organizations, accepting the consortium membership model.

---

## 📊 Comparison at a Glance

| Software | License | Stack | SSO | SCIM Provisioning | MCP Support | Self-Hosted | Best For |
|----------|---------|-------|-----|-------------------|-------------|-------------|----------|
| **BrowserStack** | Proprietary | Cloud | ✅ SAML/OAuth | ✅ SCIM 2.0 | ❌ | ❌ | QA-native IAM |
| **Okta** | Proprietary | Cloud | ✅ | ✅ | ❌ | ❌ | Enterprise vendor-neutral |
| **Entra ID** | Proprietary | Cloud | ✅ | ✅ | ❌ | ❌ | Microsoft ecosystem |
| **Ping Identity** | Proprietary | Cloud | ✅ | ✅ | ❌ | ❌ | AI-driven fraud/risk |
| **Keycloak** | Apache-2.0 | Java | ✅ | ✅ (26.8+) | ❌ | ✅ | Proven OSS IAM foundation |
| **Casdoor** | Apache-2.0 | Go/React | ✅ | ✅ | ✅ Built-in | ✅ | AI-native + MCP |
| **Authentik** | MIT core | Python/Go | ✅ | ✅ SCIM source | ❌ | ✅ | Flexible flow engine |
| **Zitadel** | AGPL-3.0 | Go/TS | ✅ | ✅ (preview) | ❌ | ✅ | Cloud-native multi-tenant |
| **Apache Syncope** | Apache-2.0 | Java | ✅ | ✅ | ❌ | ✅ | Standards-based IGA |
| **midPoint** | Open Source | Java | ✅ | (Check) | ❌ | ✅ | Full IGA governance |
| **Shibboleth** | Open Source | Java | ✅ | (Check) | ❌ | ✅ | Federated education |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source QA Identity or Access Management tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem **splits** between **full IAM platforms** (Keycloak, Casdoor, Authentik, Zitadel) that handle SSO, SCIM, and RBAC in one system, and **identity governance systems** (Apache Syncope, midPoint) that add lifecycle automation and access certifications. **BrowserStack's IAM** is the most purpose-built for QA teams, with native SSO/SCIM and product-level RBAC [citation:4]. Among open-source options, **Casdoor** is notable for its built-in MCP server and broad protocol coverage [citation:6], while **Keycloak** remains the most battle-tested foundation with SCIM support added in version 26.8 [citation:6].

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
