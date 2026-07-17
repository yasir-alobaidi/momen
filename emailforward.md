# Google Business Profile (GBP) API Integration & POC Blueprint

This document acts as the master record for setting up a Proof of Concept (POC) for "Project A" utilizing a verified Google Cloud Project and Google Business Profile belonging to "Project B" (your partner's project), alongside custom email domain configurations through Cloudflare and Gmail.

---

## 1. System Architecture (The "Two-Project" Setup)

To develop Project A safely without risking a Google restriction or policy block, the infrastructure is split between a **Consumer** application and a **Resource** data provider.

*   **Project B (Partner Project):** Acts as the **Resource / Data Source**. It contains the verified GBP listing (maturing to 60+ days) and the approved GBP API access.
*   **Project A (Your App Platform):** Acts as the **Consumer / Backend**. It executes code, runs AI routines, and provides the UI, but relies entirely on OAuth credentials generated inside Project B.

### The OAuth Flow Strategy
Instead of Project A making direct API calls via its own independent (and unverified) cloud credentials, your code will prompt a "Sign in with Google" flow utilizing Project B's Client IDs. When your friend/partner signs in with the Google Account that manages the verified GBP listing, Project A receives the access tokens required to pull locations and manipulate reviews.

---

## 2. Step-by-Step Implementation Plan

### Step 1: Generate OAuth 2.0 Credentials (On Project B)
1. Navigate to **Google Cloud Console** under **Project B**.
2. Go to **APIs & Services > Credentials**.
3. Create an **OAuth 2.0 Client ID** configured as a *Web Application*.
4. In the **Authorized Redirect URIs**, supply the exact staging/local route of your platform code (e.g., `http://localhost:3000/auth/google/callback`).

### Step 2: Implement "Sign in with Google" on Project A
In the Project A application engine, initiate the authentication handshake using Project B's newly minted `Client ID` and `Client Secret`.
*   **Required Scopes:** Ensure your auth configuration requests `https://www.googleapis.com/auth/business.manage` to allow administrative actions over reviews and profiles.

### Step 3: Fetch Locations and Reviews (Core API Endpoints)
Once authorized, use the returned `access_token` or `refresh_token` to interface with Google's endpoints:
*   **To List Locations:**
    ```http
    GET [https://mybusinessbusinessinformation.googleapis.com/v1/accounts/](https://mybusinessbusinessinformation.googleapis.com/v1/accounts/){accountId}/locations
    ```
*   **To Fetch Reviews:**
    ```http
    GET [https://mybusiness.googleapis.com/v4/accounts/](https://mybusiness.googleapis.com/v4/accounts/){accountId}/locations/{locationId}/reviews
    ```

### Step 4: Hook Up the AI Auto-Reply (Human-In-The-Loop Safeguard)
Google strictly forbids fully autonomous actions on user profiles without user oversight.
1. Pull the review body into the backend.
2. Route the text to your LLM (Gemini/GPT) to draft a professional response.
3. **Drafting Phase:** Render this generated text inside your Project A UI along with a manual **"Approve & Post"** button.
4. Upon confirmation, execute a `PUT` command to push the reply live:
    ```http
    PUT [https://mybusiness.googleapis.com/v4/accounts/](https://mybusiness.googleapis.com/v4/accounts/){accountId}/locations/{locationId}/reviews/{reviewId}/reply
    ```

---

## 3. Strict Policies & Compliance Safeguards
*   **The 30-Day Data Rule:** Google explicitly bans permanent caching of GBP assets. Your database routines must erase or forcefully refresh stored review and location records every 30 days.
*   **Migrating to Project A (The LLC Launch):** Once the concept is proven and the corporate structure (LLC) is established:
    1. Spin up an independent Google Cloud workspace for Project A.
    2. Deploy a clean corporate website showcasing its specific toolsets.
    3. File a formal application for **Basic API Access** under Project A.
    4. Hot-swap the OAuth Client keys in your backend codebase to completely detach from Project B.

---

## 4. Google API Pre-Application Checklist
When Project B hits its 60-day maturity threshold and you submit the paperwork for structural API permissions, reviewers manually inspect your digital presence. Ensure the following items are functional:

1.  **Custom Domain Landing Page:** Live, operational, and accurately reflecting the name tied to the Google Cloud Project.
2.  **Legal Artifacts:** A working Privacy Policy and Terms of Service page detailing how user Google authentication profiles are utilized and processed.
3.  **OAuth Consent Configuration:** In Google Cloud Console, ensure your application name, authorized domains list, support emails, and privacy policy URLs are perfectly aligned.
4.  **Business Justification Text:** Write a granular, system-focused paragraph explaining precisely why you need programmatic capabilities (avoid vague phrases like *"We want to manage reviews"*).

---

## 5. Free Custom Domain Email Setup (Cloudflare + Gmail)

To communicate with Google's API team natively and professionally for $0/mo, utilize Cloudflare's inbound mail rerouting and marry it to a standard Gmail SMTP channel.

### Phase 1: Cloudflare Inbound Configuration
1. Open your **Cloudflare Dashboard** and select your target domain.
2. Navigate to **Compute > Email Service > Email Routing**.
3. Accept the prompt to sync recommended MX and SPF settings directly into your DNS zone files.
4. Under **Destination Addresses**, add your personal `@gmail.com` mailbox and clear the activation prompt sent to it.
5. Under **Routing Rules**, map a clean handle (e.g., `contact@yourprojectb.com`) to target your personal inbox.

### Phase 2: Gmail Outbound Configurations
1. Go to your **Google Account Settings** (myaccount.google.com) -> Enable 2-Step Verification.
2. Navigate to **App Passwords** -> Create a key titled "Cloudflare Alias" -> Copy the generated **16-digit secret token**.
3. Head to desktop **Gmail** -> **Settings (Gear)** -> **See all settings** -> **Accounts and Import**.
4. In **Send mail as**, click **Add another email address**.
5. Input your corporate custom email (`contact@yourprojectb.com`), ensuring *Treat as an alias* is active.
6. Supply the following infrastructure variables on the prompt:
    *   **SMTP Server:** `smtp.gmail.com`
    *   **Port:** `587`
    *   **Username:** Your standard `@gmail.com` account handle
    *   **Password:** *Your 16-digit Google App Password*
7. Validate using the verification string routed into your primary dashboard.

### Phase 3: Deliverability and Anti-Spam Protocols (DNS Rules)
To guarantee outgoing messages pass security firewalls and reach Google's team successfully, add or append the following target configurations to your **Cloudflare DNS Management Console**:

#### SPF Rule (TXT Record)
*   **Type:** `TXT`
*   **Name:** `@`
*   **Value:** `v=spf1 include:_spf.mx.cloudflare.net include:_spf.google.com ~all`
*(Note: If an SPF string already exists, unify them using the schema above into a single line.)*

#### DMARC Rule (TXT Record)
*   **Type:** `TXT`
*   **Name:** `_dmarc`
*   **Value:** `v=DMARC1; p=none; rua=mailto:contact@yourprojectb.com`


the current app password is `kvzp nyec yjfu rdpo`
the app password is stored in your password manager / secrets store — **do not put it in this file**. (A real app password was found here in plaintext during review on 2026-07-17 and has been redacted; revoke it in Google Account → Security → App Passwords and generate a fresh one if SMTP send-as is still needed.)
```***