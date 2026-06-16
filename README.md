# Kook SMS Terms Landing Page

A single-page static site that serves as the **verifiable Call to Action (CTA)** for Kook's
A2P 10DLC campaign registration on Twilio. The page describes the SMS program, the opt-in
mechanism, and the required TCPA/CTIA disclosures.

## Why It Exists

Twilio rejected the A2P 10DLC campaign because the opt-in flow (a QR code on a physical
product insert card) couldn't be verified by the reviewer. This page gives them a URL they
can visit to confirm the opt-in mechanism exists and meets carrier requirements.

**Twilio campaign page (for reference):**
https://console.twilio.com/us1/develop/sms/regulatory-compliance/campaigns/BNfc8fba8423696af2ad6f556931a72891/CMe6f1fe98ff51cf6bdeb5078666b9d194

## Architecture

- **Single file:** `index.html` at repo root (Vercel requires this exact naming — no subdirectory)
- **No backend, no build step, no frameworks**
- **CDN-only** for external resources (Google Fonts)
- **Mobile-responsive** — reviewers may check on any device

## Deploy Flow

1. GitHub repo: `kook-sms-terms` on the `zalmywork` account
2. Push `index.html` to repo root
3. Connect repo to Vercel (same flow as `troy-ave-rental`)
4. Default Vercel URL will be something like `kook-sms-terms.vercel.app`
5. Use that URL in the Twilio campaign form

## Placeholders To Update Before Go-Live

| Placeholder | Where | Replace With |
|---|---|---|
| `(XXX) XXX-XXXX` | Phone number displayed on page | The actual Twilio phone number for this campaign |
| `KOOK` | Default opt-in keyword | Whatever keyword(s) the QR code pre-fills in the SMS compose screen |
| Insert card photo | "How It Works" section (commented-out `<img>`) | Optionally add a real photo of the physical insert card. A photo significantly strengthens CTA verification. |

## Page Content Requirements (Do Not Remove)

The page **must** contain all of the following for A2P 10DLC CTA compliance:

- Program name and operating company
- What types of messages consumers will receive
- Message frequency disclosure
- "Message and data rates may apply"
- Opt-in mechanism description (QR code on physical product insert)
- Opt-in keyword(s)
- Opt-out instructions (reply STOP)
- Help instructions (reply HELP)
- Link to privacy policy: https://shopkook.com/policies/privacy-policy
- Link to terms of service: https://shopkook.com/policies/terms-of-service

## After Deployment: Twilio Form Updates

### 1. CTA / opt-in description (rewrite to):
> Customers opt in by scanning a QR code on a physical product insert card included with their
> Amazon order. Full SMS program details and opt-in disclosures are available at [DEPLOYED_URL].
> The QR code opens the customer's native messaging app with our phone number and a pre-filled
> keyword (e.g., KOOK). The customer must manually press send to initiate the conversation. No
> messages are sent until the customer texts first. Customers can opt out at any time by replying STOP.

### 2. Opt-in keywords (currently blank — must fill):
> Jar, Stack, Cereal, Pasta50, Pasta

### 3. Opt-in message (currently blank — must fill):
> Thanks for reaching out to Kook! You've opted in to receive order follow-up, product tips, and
> support messages. Msg frequency varies. Msg&Data rates may apply. Reply HELP for help, STOP to opt out.

### 4. CTA verification URL:
Add the deployed page URL wherever the form accepts a verification link.

## Brand Context

- **Kook** — kitchen products brand sold on Amazon
- **Parent company:** Somerset Street Inc
- **Existing site:** https://shopkook.com
- **Use case:** Post-purchase customer engagement. Customers buy on Amazon, find an insert card
  in the box, scan the QR code, text a keyword, and enter a conversational SMS flow (satisfaction
  check-in, review request, discount offer, support).
