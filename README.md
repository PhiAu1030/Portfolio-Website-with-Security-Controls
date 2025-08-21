# Portfolio-Website-with-Security-Controls
Built a portfolio website with HTML, CSS and JavaScript, and then implemented security controls aligning with OWASP practices.
This is focused on the security controls and design choice behind it. 
Portfolio: (link) 

---

# Project Overview
- Technology: HTML, CSS, JavaScript, VSCode
- Theme: HUD-style interface with boot up animation, circuits connecting to node navigations, with matrix background
- Layout: Used a dual Desktop and Mobile version where it auto switches based on screen being landscape vs portrait mode via a main html file
- Interactivity: Sound effects when hovered over nodes, dynamic SVG circuit lines, and responsive scaling

---

# Security Controls for both Desktop and Mobile HTML
1. Iframe Sandboxing
- Loading both inside sandboxd iframes
- Restricts iframe priviledges and reduces clickjacking
- OWASP ASVS 2.13

2. Hardened postMessage Origin Checks
- Replacing insecure wildcard with explicit origin checks
- This ensures cross-frame communications can only occur from trusted origin
- OWASP ASVS 5.2.7

3. No Inline Event Handlers
- No Inline JavaScript or onclick used
- All logic is handled in <script> blocks
- The site is prepared for strick Content Security Policy (CSP)
- OWASP ASVS 14.3

4. No Third-Party Remote JS
- There are no external CDNs or remove JavaScript dependencies
- This elminates supply-chain risk
- OWASP ASVS 14.2

5. Deployment Headers
- Strengthens security at the hosting later where a _headers file is included
