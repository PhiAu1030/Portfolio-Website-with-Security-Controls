# Portfolio-Website-with-Security-Controls
Built a portfolio website with HTML, CSS and JavaScript, and then implemented security controls aligning with OWASP practices.
This is focused on the security controls and design choice behind it. 

Live Site of Portfolio: https://phiauvuportfolio.netlify.app/ 

---

# Project Overview
A sci-fi HUD themed interface with animated circuits, glowing borders, and node-based navigation. The project uses two pur[ose-built UIs:
Desktop: A widescreen with stronger effects
Mobile: portrait focused and simplified layout

Goal: Showcase front-end alongside security awareness with practical deployment controls.


---

# Archtecture (HTML, CSS, JS)
- Index: The controller of the website to load both UIs
- Desktop: Full Experience on the big screen
- Mobile: For portrait/vertical screens

I chose two UIs because due to the desktop HUD layout (circuits, big HUD, and nodes) responsive pages were out of reach. Creating the two UIs implemented an alternative to responsiveness. 

Note: The website is optimized for desktop portrait/landscape and mobile portrait only. Mobile landscape is intentionally not supported to keep UX clean and predictable.

---

# Features 
- Animated HUD (inner border glow, and boot sequence)
- Node navigation with section syncing
- Mobile for vertical/portrait layout, Desktop horizontal/landscape layout
- Harden deployment headers (CSP, XFO, referrer, etc.)
- No inline JS, self-hosted scripts and assets
- Used Netlify with '_headers' for security controls

---

# Security Controls for both Desktop and Mobile HTML
1. Iframe Sandboxing
- Loading both inside sandboxed iframes
- Restricts iframe privileges and reduces clickjacking risks
- OWASP ASVS 2.13

2. Hardened postMessage Origin Checks
- Replacing insecure wildcard '*' with explicit origin checks
- This ensures cross-frame communications can only occur from trusted origin
- OWASP ASVS 5.2.7

3. Least Privilege UI
- Prevents Interaction during load; minimizes automated or accidental actions
- OWASP ASVS 1.1

4. No Inline Event Handlers
- No Inline JavaScript or onclick used in HTML elements 
- All logic is handled in <script> blocks using addEventListener
- The site is prepared for strict Content Security Policy (CSP) enforcment 
- OWASP ASVS 14.3

5. No Third-Party Remote JS
- There are no external CDNs or remote JavaScript dependencies
- This eliminates supply-chain risk
- OWASP ASVS 14.2

6. Deployment Security Headers
- Strengthens security at the hosting layer where a _headers file is included
- CSP - blocks inline/remote code, it enforces HTTPS and prevents clickjacking
- HSTS - this enforces HTTPS across subdomains
- X-Frame Options in depth for clickjacking defense
- X-Content-Type-Options - nosniff for MIME sniffing protection
- Referrer-Policy - strict-origin-when-cross-origin
- Permission-Policy - disables camera, mic, and geolocation

---

# Lessons Learned & Key Takeways
This Project not only demonstrates front-end design but practical applications of OWASP security controls. Applying sandboxing, strict origin checks, least privilege principles, CSP readiness and secure headers, The portfolio site is resilient against common web threats.

---

# References
- [OWASP Application Security Verification Standard (ASVS)](https://owasp.org/ASVS/)  
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)  
