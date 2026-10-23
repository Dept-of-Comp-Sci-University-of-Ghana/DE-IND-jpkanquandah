# IA05 API contract (link builder)

IA05 evidence for jpkanquandah. Feature: customer enquires about a crane service (WhatsApp Enquire button). Synthetic examples only.

## Purpose and contract

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Item                         Definition
  ---------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Role, goal, value            As a customer, I want Enquire to open WhatsApp with the right number and a message about my service, so I do not type it all

  Caller                       The Enquire button on the Services section (and the “Not sure?” button)

  Provider                     The link builder function in the front-end code

  NFR or constraint            Always use the approved number (NFR-12); store nothing (NFR-24)

  Operation                    buildWhatsAppLink(serviceId) returns a link string (non-HTTP equivalent of GET /enquiry-link)

  Final link form              https://wa.me/\<approved number, digits only\>?text=\<URL-encoded message\> (example: https://wa.me/233XXXXXXXXX?text=Hello%2C%20I%20would%20like%20to%20ask%20about%20Mobile%20Crane%20Hire.)

  Path or query parameters     serviceId (text, required for a service enquiry; omitted for the general message)

  Headers and authentication   None. The function runs in the visitor’s browser.

  Authorization                None for visitors. Changing the number or service list is controlled by GitHub review and CODEOWNERS.
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Request fields:**

  --------------------------------------------------------------------------------------------------------------------------------------------------
  Field                       Type             Required   Meaning
  --------------------------- ---------------- ---------- ------------------------------------------------------------------------------------------
  serviceId                   text             Optional   Id of a service in the site content, for example “mobile-crane-hire” (synthetic example)

  Message template (config)   text             Required   The fixed sentence with a place for the service name

  Number (config)             text of digits   Required   Approved WhatsApp number, international format, no plus or spaces
  --------------------------------------------------------------------------------------------------------------------------------------------------

## Validation rules (5)

-------------------------------------------------------------------------------------------------------------------------
  \#   Rule                                                                          Kind       Checked by
  ---- ----------------------------------------------------------------------------- ---------- ---------------------------
  1    serviceId must be text                                                        Type       link builder

  2    serviceId must match a service in the content list                            Business   link builder

  3    The number must be digits only, 10 to 15 digits                               Format     config check or test

  4    The message must be URL-encoded so spaces and symbols do not break the link   Format     link builder, tests TC-08

  5    The number used must be the approved number                                   Business   tests TC-06 and TC-19
  -------------------------------------------------------------------------------------------------------------------------

## Success response

Outcome: a link is returned and the browser opens WhatsApp. Synthetic example response:

    {
      "ok": true,
      "link": "https://wa.me/233000000000?text=Hello%2C%20I%20would%20like%20to%20ask%20about%20Mobile%20Crane%20Hire.",
      "service": "Mobile Crane Hire"
    }

Fields: ok says it worked; link is what the button opens; service is the name used in the message. Next display: WhatsApp opens with the message ready to edit. (The real function may return only the link string. The JSON is how I describe the contract.)

