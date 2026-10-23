# IA07: Test Evidence, PR Review and CI Walkthrough

**Identity:** jpkanquandah, team Intellectuals. Repositories: https://github.com/Dept-of-Comp-Sci-University-of-Ghana/DE-IND-jpkanquandah and https://github.com/Dept-of-Comp-Sci-University-of-Ghana/dcit208-client-project-2026-team-engineering-repository-intellectuals. Issue: (link in the Sakai portfolio). PR: (link in the Sakai portfolio). Date: 23 October 2026.

## Feature context

-   **User:** customer on a phone. **Feature:** Enquire button opens WhatsApp with a prepared message.
-   **Requirement and story:** NFR-12 (right number), story “As a customer, I want to tap Enquire…”.
-   **Acceptance criteria:** AC1 right number and service name; AC2 fallback when WhatsApp cannot open (see IA03).
-   **Client value:** enquiries reach the owner without repeated DMs.
-   **Status (honest):** the Enquire button is implemented on the deployed site; the automated link-builder tests below are planned checks unless marked otherwise.

## Six test cases

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  \#   Type                        Starting condition                       Action                             Test data                              Expected result                                                           Status and evidence
  ---- --------------------------- ---------------------------------------- ---------------------------------- -------------------------------------- ------------------------------------------------------------------------- -------------------------------------
  1    Normal                      Services section open                    Tap Enquire on a service           Service “Mobile Crane Hire (sample)”   WhatsApp link has the approved number and the service name                Planned (not yet run by me)

  2    Invalid input               Link builder called with an unknown id   Call buildWhatsAppLink             id “xyz”                               General message link; no crash                                            Planned (not yet run by me)

  3    Edge                        Service name with special characters     Build the link                     “Heavy & Wide Loads: 50% off”          Message is correctly URL-encoded, link still opens                        Planned (not yet run by me) (TC-08)

  4    Authorization or security   A change edits the number                Open a PR changing the number      Fake number 233111111111               Review is required; tests fail if it is not the approved number (TC-19)   Planned (not yet run by me)

  5    Failure or dependency       Phone without WhatsApp                   Tap Enquire                        Any service                            Phone shows WhatsApp page; Contact section still shows the number         Planned (not yet run by me)

  6    Regression                  After a navigation change                Open the phone menu and tap Home   None                                   Home opens and all Enquire buttons still work                             Planned (not yet run by me)
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Safe test data

All test data is synthetic: made-up service names, the number 233000000000 and a fake number for the security test. I chose special characters on purpose to test encoding. No real client records, real customer chats or credentials are used.

## PR review and CI

**Planned PR review checklist** (to be used on the Enquire button pull request, (link in the Sakai portfolio), or on a future PR):

-   [ ] Requirement fit: the change matches the story and acceptance criteria.
-   [ ] Validation: ids, number and message are handled.
-   [ ] Tests: new or changed code has tests and they pass.
-   [ ] Data risk: no customer data or real private details added.
-   [ ] Security: number unchanged unless approved; no new third-party scripts.
-   [ ] Documentation: README or content notes updated.
-   [ ] AI disclosure: the PR says whether AI was used.
-   [ ] System impact: nothing else (menu, images) breaks.

**CI:** our team pipeline is meant to run lint, test and build on every pull request, and make test runs the same checks locally. Commands to run: make setup, make lint, make test. No CI run log is attached to this report and I am not claiming a successful run. The team must improve: add a test job for the link builder that fails if a link does not start with the approved number, and require CI to pass before merging.

## Defect walkthrough

**Likely defect:** a service name with an ampersand or percent sign is not encoded, so the message is cut off in WhatsApp.

-   **Reproduction:** put a service called “Heavy & Wide Loads” in the content, tap Enquire.
-   **User-visible result:** the chat opens with only “Hello, I would like to ask about Heavy”.
-   **Evidence:** the generated link in the browser address bar, the failing unit test.
-   **Fix:** encode the message with encodeURIComponent and add test 3 so it cannot come back.

## Video and AI disclosure

-   Video (3 to 4 minutes, covering feature, tests, PR focus, CI and one weakness): https://youtu.be/bMEDxWQgDD4. Files in IA07/.
-   **AI used:** Yes. Claude (Anthropic), 23 October 2026: drafted the test table and checklist. I changed the test data to synthetic values and marked every test as planned because I have not run them. My own understanding: the Enquire link is only as safe as the number and encoding behind it, so tests should check both.

