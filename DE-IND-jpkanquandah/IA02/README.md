# IA02: Client Interview Evidence and Requirement Transformation Memo

**Identity:** jpkanquandah, team Intellectuals, LiftPro Crane Services Website, date 23 October 2026.

## Personal question set (written before the conversation)

Twelve questions: three on workflow, two on pain points, two on data, two on success criteria, one on security and privacy and two on failures and exceptions.

  ----------------------------------------------------------------------------------------------------------------------------------------
  **Topic**             **Question**
  --------------------- ------------------------------------------------------------------------------------------------------------------
  Workflow              1\. Walk me through what happens from the moment someone messages you about a crane job until the job is agreed.

  Workflow              2\. Where do most of your customers find you today, and on which device do they usually message you?

  Pain point            3\. Which questions do customers ask you again and again?

  Pain point            4\. What takes most of your time when you answer enquiries by direct message?

  Data                  5\. Which services should the website list, and who gives us the names, descriptions and photos?

  Data                  6\. Which phone number and business details should appear on the site?

  Success criteria      7\. How will you know the website is working for you after one month?

  Success criteria      8\. What must a customer be able to do on the site within a few taps?

  Security / privacy    9\. Do you want the site to collect any customer details, or should customers only message you on WhatsApp?

  Failure / exception   10\. What should happen if a customer does not have WhatsApp on their phone?

  Failure / exception   11\. What do you do today when you cannot take a job, and should the site say so?

  Workflow              12\. Who will keep the services and photos up to date after the project ends?
  ----------------------------------------------------------------------------------------------------------------------------------------

## Authentic interview or observation evidence

**Date and medium:** 3 October 2026, phone call with the client (first-contact evidence, team charter D0 section C.4). **Participant role:** Bernard Nyantakyi, owner and operator of the crane business in Madina. **Evidence type:** call notes and a call screenshot stored with the team’s charter evidence; private details are redacted in this report. **My part:** (link in the Sakai portfolio).

**Summary of what the client said:** The client is a mobile crane operator in Madina who posts videos of his work on TikTok and Instagram Stories. Many people message him directly to ask what services he offers and how much a particular service costs. Answering the same questions one by one takes his time, and his services are not shown together in one place. He asked for a website that shows his mobile crane services and has a button that sends visitors straight to his WhatsApp line so they can make their enquiries there. He did not ask for online booking or for the site to collect customer details.

## Requirement transformation

**Raw client statement (faithful paraphrase from our intake call):** The client wants a website that shows his mobile crane services and has a button that sends visitors straight to his WhatsApp line, so that they can make their enquiries there. I use a paraphrase because I do not have an exact recorded quote.

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Item                           My answer
  ------------------------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Functional requirement         When a visitor taps Enquire on a service, the site shall open a WhatsApp chat with the owner’s approved number and a prepared message that names that service.

  Non-functional requirement     The Services section shall load and show its Enquire buttons within 3 seconds on a typical mobile connection (checked by opening the live site on a phone on mobile data).

  User story                     As a customer, I want to tap Enquire on a crane service, so that I can ask the owner about it in WhatsApp without typing the details myself.

  Acceptance criteria            AC1: Given I am on the Services section, when I tap Enquire on a service, then WhatsApp opens with the owner’s number. AC2: The message text includes the name of that service. AC3: I can edit the message before I send it. AC4: If I tap “Not sure? Ask the owner”, a general message opens instead. AC5: The website does not ask me to type or store any personal data.

  Interface or API implication   A link builder takes a service and returns a WhatsApp link with the approved number and an encoded message. There is no server API.

  Data implication               A list of services and one configuration place for the number and message template, held in the site content (no database).

  Test idea                      Click Enquire on each service and check the number and the service name in the opened link (a unit test for the link builder).

  Open question                  Does the client want prices or availability on the site later, or only in the chat?
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Map of interface, data, validation and risk:**

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Interface                          Data                                              Validation                                                   Risk
  ---------------------------------- ------------------------------------------------- ------------------------------------------------------------ --------------------------------------------------
  Enquire button on each service     Service name, approved number, message template   Message is URL-encoded; number comes from one config place   Wrong number sends enquiries to the wrong person

  “Not sure? Ask the owner” button   General message template                          Same link builder                                            Customer sends a vague message
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Reflection (about 300 words)

Before the call I assumed a business like this would want a full website with prices, availability and maybe online booking. I imagined the site as a kind of shop window with a form. After reading the client’s own words from the call, I saw that his real problem is smaller and more practical: people already find him on TikTok and Instagram, and the time he loses is spent answering the same questions in direct messages. He wants customers to see his services in one organised place and then reach him on WhatsApp, which he already uses all day.

That made my assumption about online booking false, and my assumption about prices weaker. He did not ask for either, and he seems to prefer to discuss prices in the chat because every job is different. An assumption that became stronger is that customers are on phones. His customers come from social media, so the site has to be fast and easy on a small screen, and that matters directly to me as the frontend developer.

What surprised me most was how much he wanted the site to do less. A form that stores customer details, which I would have added without thinking, would actually create work and risk for him. It also changed how I wrote the requirement. I wrote it around one tap on Enquire that opens WhatsApp with the service name already in the message, instead of around a booking process. I also added the acceptance criterion that the site does not ask for or store personal data, and a fallback for visitors who cannot open WhatsApp.

I am still unsure whether he will later want prices or availability on the site, so I recorded it as an open question rather than guessing. The main thing I learned is that a requirement should come from what the client says his customers actually do, not from what I think a business website normally has.

## Team files, branch and AI disclosure

-   Branch: ia2-jpkanquandah-client-discovery. Commit: IA2: add jpkanquandah individual evidence. PR: IA2 Evidence - jpkanquandah. (link in the Sakai portfolio)
-   Team files updated: docs/00-client-brief.md, docs/01-requirements.md, docs/09-system-design/requirement-to-system-map.md and the client meeting minutes (to be confirmed in the PR description).
-   **AI used:** Yes. Claude (Anthropic), 23 October 2026: drafted the question list, the table layout and a first version of the reflection from our D0 charter. I changed the wording, removed any claim I could not support from our evidence, and compared the text with the client intake notes in D0. No video is required for IA02.

