# IA10: Final Individual System Defence and Contribution Evidence

**Identity:** jpkanquandah, team Intellectuals, LiftPro Crane Services Website. Repositories: https://github.com/Dept-of-Comp-Sci-University-of-Ghana/DE-IND-jpkanquandah and https://github.com/Dept-of-Comp-Sci-University-of-Ghana/dcit208-client-project-2026-team-engineering-repository-intellectuals. Final release tag: (link in the Sakai portfolio). Date: 23 October 2026.

## My contribution and evidence

**Contribution I chose:** feature (frontend).

**What I did and why it mattered:** As the team’s Frontend Developer I built the pages a visitor sees on a phone, including the Services section, the gallery and the WhatsApp Enquire button, and checked them on different screen sizes. This mattered because the client’s customers arrive from TikTok and Instagram on phones, and the Enquire button is the whole reason the site exists: it turns a visitor into a WhatsApp chat with the owner. Without it the client would keep answering the same questions by direct message.

**Supporting need and evidence:**

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Item                                    Link or detail
  --------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------
  Requirement, story or NFR               Story: As a customer, I want to tap Enquire on a crane service so that I can ask the owner in WhatsApp. NFR: every WhatsApp link uses the approved number.

  Client need                             Customers need one clear place to see services and message the owner

  Issue                                   (link in the Sakai portfolio)

  Pull request                            (link in the Sakai portfolio)

  Commit                                  (link in the Sakai portfolio)

  Review comment                          (link in the Sakai portfolio)

  Test, document, release or deployment   (link in the Sakai portfolio)
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## System impact and verification

**Where it fits:** customer → phone browser → crane-mobile.vercel.app → Services section → Enquire button → link builder → WhatsApp. The front end I built is the only part the customer touches; the host serves the static files and WhatsApp receives the message.

**Verification evidence:** I checked the Services section and Enquire buttons on phone and desktop sizes and by tapping each button to see the opened chat.

**One honest limitation:** I have not load tested the site, there is no booking or price information, and the free hosting plan may not allow business use (ADR-003).

**One realistic next improvement:** add real photos from the client and train a helper to update the services content, then add an automated test for the link builder.

## D10 cross-reference (non-confidential, not an extra marked section)

  ---------------------------------------------------------------------------------------------------------------------------------------------------------
  Item                                  Entry
  ------------------------------------- -------------------------------------------------------------------------------------------------------------------
  Role                                  Frontend Developer (deputy: Mireku Justice)

  Commits                               (see GitHub Insights)

  PRs authored and reviewed             (see GitHub Insights)

  Issues owned                          (see GitHub Insights)

  Documents and tests                   (link in the Sakai portfolio)

  Client or team contributions          Frontend pages for the client’s services, gallery and WhatsApp enquiry, and responsive checks across screen sizes
  ---------------------------------------------------------------------------------------------------------------------------------------------------------

**What problem did I solve?** Visitors had no single place to see the client’s crane services or reach him easily. **What did I design?** The mobile layout of the Services section and the Enquire button flow. **What did I implement?** The Services section, gallery and WhatsApp Enquire button on the front end. **How did I test it?** By opening the site on phone and desktop sizes and tapping every Enquire button to check the number and message. **What would I improve?** Add automated tests for the link builder and use real photos.

**One code file I can defend:** (link in the Sakai portfolio). **One test file:** (link in the Sakai portfolio). **One requirement:** UC-02, customer enquires about a crane service. **One design decision:** the static site with a wa.me link and no back end or database (ADR above).

**Responsible AI use, and what I learned without AI:** I used Claude to draft structure and wording, and to suggest layouts for my drawings, but I drew the diagrams myself and I must be able to explain every statement in this portfolio. Without AI I learned how a phone browser loads our static page from Vercel, how a wa.me link carries a number and an encoded message, and why a small wrong detail like the wrong number or a missing encoding can send a customer to the wrong place.

## Video and AI disclosure

-   Video (4 to 5 minutes): https://youtu.be/bMEDxWQgDD4.
-   **AI used:** Yes. Claude (Anthropic), 23 October 2026: drafted wording for this section and the others. I changed it to describe my frontend work and checked it against the team charter (D0). I kept the parts only I can confirm (links, commit counts, file paths) highlighted for me to fill from GitHub.
-   The confidential peer note is a separate private Sakai attachment and is **not** included here.
