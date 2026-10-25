# IAM Labs

I'm Landon Alexander, a Cybersecurity and Information Assurance student at Frostburg State University. This is where I document my Identity and Access Management labs.

Every lab here is built like a real IAM project. I make up a company, work through tickets, plan the build before I touch any settings, and then prove the security actually works. In every write-up I explain what I did and why I did it, in a way that makes sense whether you work in security or not.

All the companies, users, and emails in these labs are fake and live in my personal lab environments.

---

## How I build

### I plan before I build

I don't start in the admin console. I start on paper. I map out the system, decide what each security control is for, and then I build it.

For my SpyTech labs I planned everything around the AAA framework:

- **Authentication: who are you?** Username and password, MFA with an authenticator app, passkeys, and SSO login.
- **Authorization: what can you get into?** Permissions on groups, users added by role, least privilege, and disabling people who leave instead of deleting them.
- **Accounting: what did you do?** Logs of sign-ins, failed sign-ins, and admin changes, with plans to send them to a SIEM later.

This is my original plan from when I first built it in Keycloak:

![AAA design notes](okta-spytech-part1-authentication/aaa_design_notes.jpg)

### I learn how it works, not just where to click

Before I relied on SSO, I drew out how it actually works. The app sends you to the identity provider, you log in once, and it remembers you with a session cookie. Every app after that gets a signed badge without making you log in again. I also wrote down the difference between the session cookie and the refresh token, because I mixed them up at first and wanted to get it right.

![SSO login flow notes](okta-spytech-part1-authentication/sso_login_flow_notes.jpg)

### I build from a checklist I trust

I keep a checklist of security controls that I know are solid, and I know what each one is there to stop. I call it my lockdown bag.

| Control | What it stops |
|---|---|
| Logging sign-ins and admin changes | Not knowing what happened |
| Password rules and lockout | Weak passwords and endless guessing |
| Change password at first login | IT knowing anyone's real password |
| MFA for everyone | A stolen password being enough to get in |
| Session limits | A stolen session working forever |
| Groups by role | People getting access their job doesn't need |
| Disable, don't delete | Losing records needed for audits |
| Named admins with MFA | Admin changes nobody can trace back |
| Extra MFA for admin changes | A hijacked admin session changing security settings |
| HTTPS in real deployments | Passwords being read as they travel |
| Passkeys | MFA codes getting phished |

### I write down every decision

While I build, I take notes on every change, where it lives, why I made it, and what I'd tighten before it went live. Those notes are in each lab, so you can see how I was thinking, not just what the end result looks like.

---

## Labs

| Lab | Tool | What it covers | Status |
|---|---|---|---|
| [SpyTech Part 1: Authentication and Accounting](okta-spytech-part1-authentication/) | Okta | MFA for all users, password and lockout rules, session limits, proof from the System Log | ✅ Done |
| SpyTech Part 2: Authorization | Okta | Apps assigned by department, least privilege, handling an access request that asks for too much | 🔜 Next |
| SpyTech Part 3: Lifecycle and Audit | Okta | Onboarding, moving, and offboarding employees, and answering an audit question from the logs | 🔜 Planned |

---

## Skills across these labs

IAM design, AAA framework, Okta, Keycloak, MFA policy, SSO with OIDC, role-based access control, least privilege, session management, logging and audit evidence, and explaining security in plain language.
