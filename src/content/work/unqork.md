---
title: Insurance Platform on Unqork
publishDate: 2024-05-24 00:00:00
img: /assets/unqork.png
img_alt: unqork Logo
description: |
    Company life insurance platform built on unqork
tags:
  - Unqork
  - Life Insurance Platform
  - Development
---

**Unfortunately, due to the platform being proprietary software I am unable to show screenshots**

## Background
In August 2021, my company was planning on moving on from a 3rd party vendor for their life insurance platform sales solution. After vetting companies, they settled on <a href="https://www.unqork.com"> unqork</a>, which is a no-code development platform-as-a-service for building enterprise applications. I was selected to spearhead the transition to the new platform which would be used by our distribution partners' agents to sell our various life insurance products.

## Integration with the rules engine
Unqork was very plug and play in terms of creating a sleek looking UI for our needs. However, one of the initial bigger projects was integrating with our rules engine (called SMARTS). How it basically worked was that this rules engine would dictate to us what questions needed to be shown for a specific product and for a specific state within a specific product. So you could have one product in AL show one set of questions and that same product in NY show different questions. The source of truth for this needed to be SMARTS so we needed a solution that could both ingest these rule sets to show the appropriate questions and also, when it came time to submit the application responses, send these responses in a way that SMARTS could read and respond back with an underwriting decision. The solution we came up with was that we built an engine inside unqork to read SMARTS and create us a skeleton for that product & inside that skeleton would also handle the state specific sections for that product. Then we would edit the skeleton's design to make it user friendly, add in any specific items that were relevant in terms of other third party integrations, and then make another engine that would dynamically read what questions were answered and send this back to SMARTS in a way that was understood by SMARTS.

## Third Party Integrations
- <a href="https://www.rxhistories.com/"> Milliman  Intelliscript</a>: Used for retrieving customers drug history for quantifying the morality risk applicants
- <a href="https://stripe.com/"> Stripe</a>: Payment vendor. For this we had to create a javascript element to render the Stripe element and then once the data is input to the front end, verify it with stripe and act accordingly.
- Boomi: these were API end points created by our internal IT team to perform various tasks such as authenticating, updating our mongoDB, interacting with our rules engine, etc.

## Data Security
Possibly the biggest hurdle facing our team was that our security team wanted no data to be stored on the unqork databases. This proved to be a challenge as information would be needed from previous pages so a mechanism needed to be created to store data safely. Furthermore, the previous platform had a resume/save functionality that would allow applicants to re-enter their application at any time and be dropped on the page they were most recently on. The solution we came up with was that we would have the IT team expose an end point to us that we could use for saving/retrieving applications based on the internal ID they were given. On the unqork side, we would dynamically save the information to this end point, and then use this same end point to retrieve all information. It would need to be dynamic because, as stated above, not all products following the same structure. Obviously some items that name, date of birth, address consistently are shown throughout all products, but there is some disparity so we needed to handle that dynamically on our side which we were able to do.