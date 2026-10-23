# IA05 error model

IA05 evidence for jpkanquandah. Feature: customer enquires about a crane service (WhatsApp Enquire button). Synthetic examples only.

## Error cases (5)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Case                                                               Outcome                                     Error code                 User-facing message                                  Logging
  ------------------------------------------------------------------ ------------------------------------------- -------------------------- ---------------------------------------------------- -----------------------------------------
  Invalid input: serviceId is not text                               No link; fall back to the general message   ERR_INVALID_SERVICE_ID     “Please ask the owner about this service.”           Console warning in development

  Authorization: someone tries to change the number without review   Change is blocked by branch protection      ERR_REVIEW_REQUIRED        Not visible to visitors; shown on the pull request   GitHub audit trail

  Conflict: serviceId matches two services (duplicate id)            Build or test fails                         ERR_DUPLICATE_SERVICE      Not shown to visitors; the change cannot be merged   CI log

  External service failure: WhatsApp cannot open                     Phone shows the WhatsApp page or an error   ERR_WHATSAPP_UNAVAILABLE   Contact section still shows the number               None on the site (nothing is collected)

  Missing configuration: number is empty                             Build or test fails                         ERR_NUMBER_MISSING         Not shown to visitors                                CI log
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Status of each error case:** ERR_REVIEW_REQUIRED is enforced today by GitHub branch protection and CODEOWNERS. The other codes (ERR_INVALID_SERVICE_ID, ERR_DUPLICATE_SERVICE, ERR_NUMBER_MISSING) are the names I give to checks that are planned in the link builder and CI tests, not confirmed in the code. ERR_WHATSAPP_UNAVAILABLE is a behaviour of the phone and WhatsApp, not of our code.

## Duplicates and retries

If a customer taps Enquire twice, two chats may open, but nothing is stored, so there is no duplicate record. The function is idempotent (the same input always gives the same link). A retry is **safe** because it only builds a link. There is no unique constraint or request id because there is no data. The one unsafe retry is the customer sending the same WhatsApp message several times, which is outside our system.

