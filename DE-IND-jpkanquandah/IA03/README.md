# IA03: Use-Case-to-Story Traceability Card

**Identity:** jpkanquandah, team Intellectuals, LiftPro Crane Services Website, client domain: mobile crane hire in Madina, date 23 October 2026.

## Source and use-case card

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Field                       Entry
  --------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Use case                    UC-02: Customer enquires about a crane service

  Source                      Client intake call of 3 October 2026 (team charter D0 section C.4): the client wants a button that sends visitors to his WhatsApp. Use case UC-02 in our team requirements documents.

  Why it matters              Enquiries are the whole reason the website exists. It removes the repeated DM questions for the client.

  Actor                       Customer (website visitor on a phone)

  Goal                        Ask the owner about a specific crane service

  Trigger                     The customer taps Enquire on a service

  Preconditions               The site is online; the customer has WhatsApp or can open the WhatsApp web link; the owner’s number is approved and set

  Main success flow           1\. Customer opens the website. 2. Customer views the Services section. 3. Customer selects a service and taps Enquire. 4. WhatsApp opens with the owner’s number and a prepared message naming the service. 5. Customer edits the message if needed. 6. Customer sends the enquiry.

  Alternate flow              The customer is not sure which service they need: they tap “Not sure? Ask the owner” and a general message opens (flow 2 in our demo).

  Exception or failure flow   WhatsApp is not installed or the link cannot open: the phone shows the WhatsApp page or an error, the customer can use the number shown in the Contact section instead.

  Postconditions              A chat with the prepared message is open in WhatsApp. The website has stored nothing.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Story, acceptance criteria and NFR

**Story:** As a customer, I want to tap Enquire on a crane service, so that I can ask the owner about it in WhatsApp without typing the details myself.

**AC1 (success), Given-When-Then:** Given I am on the Services section on my phone, when I tap Enquire on a service, then WhatsApp opens with the owner’s approved number and a message that includes that service’s name.

**AC2 (error path):** Given WhatsApp cannot open from the link, when I tap Enquire, then I can still find the owner’s number and location in the Contact section and contact him another way.

**NFR category:** Reliability and correctness of the contact number. **NFR:** Every WhatsApp link on the site shall use the approved number. **Why it matters:** if the number is wrong, the client loses customers and customers reach a stranger. **What “secure” means here:** only the approved number is ever used, only the team can change it through a reviewed pull request, and the site stores no customer data. **What “fast” means here:** the page and Enquire buttons are usable within about 3 seconds on mobile data.

## Traceability row

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Source                           Use case   Story                     NFR                   Issue                                                                                                                                          AC         Test idea                                                                                                                                                                                Status
  -------------------------------- ---------- ------------------------- --------------------- ---------------------------------------------------------------------------------------------------------------------------------------------- ---------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------
  Client intake: WhatsApp button   UC-02      Enquire about a service   NFR-12 right number   UC-02: Customer enquires about a crane service (WhatsApp Enquire button). URL: (link in the Sakai portfolio)   AC1, AC2   Test name: TC-06 link uses the approved number. Input: service “Mobile Crane Hire (sample)”. Expected: link starts with the approved number and the message contains the service name.   Planned (test not yet run by me)

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Request-flow reasoning

  ------------------------------------------------------------------------------------------------------
  Question                     Answer
  ---------------------------- -------------------------------------------------------------------------
  Actor device and interface   Customer’s phone, mobile browser

  Screen, route or endpoint    Services section of https://crane-mobile.vercel.app/, then a wa.me link

  Data sent                    Only a page request; the link carries the number and message text

  Validation                   The message is URL-encoded; the number comes from one config place

  Database or service          None; WhatsApp is the external service

  Response                     Static page; WhatsApp chat with prepared message

  Validation failure           Missing service name or bad number is caught by tests and review

  Outage                       Hosting or WhatsApp down: page or chat cannot open

  Failure point                The link content (wrong number or broken encoding)

  Protected data or concern    The approved number, and customer privacy (nothing stored)
  ------------------------------------------------------------------------------------------------------

## Declaration and AI disclosure

“I understand the use case, story, acceptance criteria and traceability links submitted here, and I can explain them orally if called upon.” Typed name: jpkanquandah

**AI used:** Yes. Claude (Anthropic), 23 October 2026: drafted the card layout from my team’s use cases. I changed the wording to match our site, and checked the use case, story and flow against our team documents. No IA03 video is required.

