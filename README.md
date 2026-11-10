# Injection Lab: insecure vs secure AI agent

An interactive demo of **prompt injection** and how to defend against it.

Two simulated agents get the same request and the same untrusted text (a web page, email, file name, or tool error). One obeys whatever it reads. The other treats it as data and asks the user before any risky action.

**Live demo:** https://YOUR-USERNAME.github.io/injection-lab/

## What it shows

| Scenario | What the text tries to do |
|---|---|
| Hidden text on a web page | Email saved passwords to an attacker |
| Urgent email | Forward invoices to an outside address |
| Fake authority | Claim to be an admin and trigger a download |
| Poisoned file name | Delete a folder |
| Booby-trapped tool error | Transfer money |
| Clean page (control) | Nothing. Proves the secure agent isn't just refusing everything |

## The core idea

- Only the user, in the chat, can give valid instructions.
- Everything the agent reads (web pages, emails, files, tool results) is **data, not commands**.
- Side-effect tools (send, delete, transfer, download) need an explicit yes from the user.

## Run it locally

No build step. Open `index.html` in a browser.

## Limits

Everything is simulated. The "model" is a small rule-based stand-in, so the demo shows the *structure* of the defense, not how a real model behaves. Text scanning can be bypassed; the dependable layers are source labelling, a gate on side effects, and user approval.

## Ideas to extend

- Swap the stand-in for a real model API call
- Add more tools and payloads
- Add automated tests with expected outcomes per payload
- Log blocked attempts with their source
