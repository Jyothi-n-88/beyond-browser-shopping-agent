# AI Shopping Co-Pilot — Multilingual Voice-First Browser Agent

> **Hackathon:** wHACKiest 2026 — Ramaiah Institute of Technology (RIT)  
> **Team:** Visionary Crew (`fdffa049`)  
> **Selected Track:** Track 2 — *Beyond the Browser: Reimagine How We Use the Web*  

---

## 1. Overview & Problem Statement

Modern e-commerce platforms such as **Amazon, Flipkart, and Meesho ,etc** are designed primarily for young, tech-savvy users. For parents, grandparents, senior citizens (60+), and vernacular first-time internet users, everyday online shopping becomes an intimidating obstacle course:

* **Visual Clutter & Information Overload:** Dense product grids, sponsored ads, tiny fonts, and dozens of filter options create cognitive fatigue.
* **Language Barriers:** Product specifications, filters, and customer reviews default predominantly to complex English.
* **Cross-Platform Comparison Fatigue:** Finding a reliable product at a fair price requires opening multiple tabs, manually applying identical filters across sites, and verifying genuine reviews against fake 5-star listings.
* **Checkout Anxiety:** Fear of ordering the wrong size, getting trapped in hidden add-ons, or making payment errors forces elders to depend entirely on younger family members.

---

## 2. Proposed Solution

We are designing a **patient, multilingual AI Chrome Co-Pilot** that lives directly inside the user's browser. Instead of forcing users to navigate complex websites, they simply speak in their native language (**Kannada, Hindi, Tamil, or English, and many more**).

The browser agent autonomously scans **Amazon, Flipkart, and Meesho** in parallel, filters out low-trust listings using a custom **Trust Score**, explains the top 3–5 genuine deals aloud in a warm, natural voice, and automates the checkout workflow right up to the final payment step.

### Core Design Principle: The 90 / 10 Safe Checkout Model
* **90% Automated by the Agent:** Voice intent extraction, multi-tab product search, variant/size filtering, Trust Score ranking, conversational Q&A, size selection, cart addition, and address confirmation.
* **10% Controlled by the Human:** The agent **always pauses safely at the Payment Screen**, requiring the user (or a trusted family member) to manually authorize UPI PIN / OTP / card payment. Zero risk of unauthorized transactions.

---

## 3. Why Track 2 (*Beyond the Browser*)?

Rather than building another standalone chatbot wrapper, our architecture transforms the browser itself into an intelligent, accessible execution environment:
* **Client-Side DOM Perception & Action:** Operates directly inside the user's active browser context to inspect page structures, apply filters, and execute multi-step navigation across competing e-commerce portals.
* **Human-Centric Web Accessibility:** Replaces cluttered visual interfaces with a high-contrast, large-button Side Panel and natural regional-language voice interaction.

---

## 4. End-to-End User Workflow

1. **Speak Request:** User clicks the microphone in the Chrome Extension Side Panel and speaks naturally *(e.g., "Find women's sports shoes, size 7, good reviews and low price")*.
2. **Parallel Multi-Store Scan:** The extension coordinates background tabs across **Amazon, Flipkart, and Meesho**, applying size, category, and budget filters.
3. **Trust Score Ranking:** The AI brain discards suspicious 5-star listings with minimal reviews and ranks the **top 3–5 genuine value options** based on rating, verified review volume, return policy, and final price.
4. **Warm Voice Summary:** Powered by **ElevenLabs**, the agent speaks back clearly in the user's chosen language, summarizing the best options.
5. **Conversational Follow-Up:** The user can ask clarifying questions *(e.g., "Does Option 2 support Cash on Delivery?")* or select a product by voice.
6. **Auto-Checkout & Safe Handoff:** The agent navigates to the chosen listing, selects the requested variant (`Size 7`), clicks **Add to Cart -> Proceed to Buy**, verifies the saved address, and stops cleanly on the **Payment Page** for manual user completion.

---

## 5. System Architecture & Planned Tech Stack

> *Note: In strict compliance with Round 1 No-Code guidelines, this repository contains architectural blueprints and design documentation only. Implementation begins on Hack Day.*

```text
+-----------------------------------------------------------------------+
|                     USER (Elder / Vernacular Shopper)                 |
|             Speaks in Kannada / Hindi / Tamil / English               |
+-----------------------------------+-----------------------------------+
                                    |
                                    v
+-----------------------------------------------------------------------+
|             CHROME EXTENSION SIDE PANEL (Manifest V3 + React)         |
|  - High-contrast, large-font UI & Mic Capture (Web Speech API)        |
|  - DOM Content Scripts (Perception & Safe Click Automation)           |
+-------------------+-----------------------------------+---------------+
                    |                                   |
                    v                                   v
+-----------------------------------+   +-------------------------------+
|    MULTI-STORE BROWSER TABS       |   |   CLOUD BACKEND & AI BRAIN    |
|  - Amazon.in                      |   |  - AWS Lambda & API Gateway   |
|  - Flipkart.com                   |   |  - LLM Intent & Trust Scorer  |
|  - Meesho.com                     |   |  - AWS DynamoDB (Preferences) |
|  (Stops at Payment Gateway - 10%) |   |  - ElevenLabs Multilingual TTS|
+-----------------------------------+   +-------------------------------+
```

### Planned Technology Stack
* **Browser Interface & Automation:** Chrome Extension (`Manifest V3`), React, Tailwind CSS, DOM Content Scripts
* **Multilingual Voice Synthesis:** **ElevenLabs API** (`eleven_multilingual_v2`) + Browser Web Speech API (STT)
* **Cloud & Serverless Orchestration:** **AWS Lambda**, **Amazon API Gateway**, **Amazon DynamoDB**
* **AI Reasoning & Ranking Engine:** Foundation LLM API (Intent extraction, attribute normalization, and Trust Score computation)

---