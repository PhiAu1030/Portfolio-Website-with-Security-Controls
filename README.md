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
- Loading both inside sandboxed iframes
- Restricts iframe privileges and reduces clickjacking
- OWASP ASVS 2.13
<img width="540" height="40" alt="sandboxing" src="https://github.com/user-attachments/assets/f1eb0860-7fd1-4d2e-a60a-ce42a34bec78" />


2. Hardened postMessage Origin Checks
- Replacing insecure wildcard with explicit origin checks
- This ensures cross-frame communications can only occur from trusted origin
- OWASP ASVS 5.2.7
<img width="695" height="63" alt="location origin" src="https://github.com/user-attachments/assets/a6a1cb97-9ae3-442f-b655-9098f47e396a" />

3. Lease Privilege UI
- Prevents Interaction during load; minimizes automated or accidental actions
- OWASP ASVS 1.1
<img width="326" height="38" alt="lock down cross frame messaging" src="https://github.com/user-attachments/assets/5a56e868-00ac-40ff-8d59-4ece13f65207" />

4. No Inline Event Handlers
- No Inline JavaScript or onclick used
- All logic is handled in <script> blocks
- The site is prepared for strick Content Security Policy (CSP)
- OWASP ASVS 14.3
<img width="939" height="431" alt="child-parent" src="https://github.com/user-attachments/assets/32438fef-8301-4f57-aa51-b553631c03ac" />

5. No Third-Party Remote JS
- There are no external CDNs or remote JavaScript dependencies
- This elminates supply-chain risk
- OWASP ASVS 14.2
<img width="855" height="468" alt="child parent 2" src="https://github.com/user-attachments/assets/750fb3a4-c285-4b6a-ae80-14a14a82549d" />

6. Deployment Headers
- Strengthens security at the hosting later where a _headers file is included
<img width="1570" height="330" alt="header script" src="https://github.com/user-attachments/assets/f821865d-bd82-421e-a71e-d31e331abf14" />

