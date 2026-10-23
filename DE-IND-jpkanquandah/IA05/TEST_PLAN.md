# IA05 contract test plan

IA05 evidence for jpkanquandah. Feature: customer enquires about a crane service (WhatsApp Enquire button). Synthetic examples only.

## Contract tests (6)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  \#   Test                       Input                                                   Expected outcome and response
  ---- -------------------------- ------------------------------------------------------- --------------------------------------------------------------------------------------------
  1    Valid request              serviceId = existing service                            ok true; link starts with wa.me and the approved number; message contains the service name

  2    Missing or invalid field   serviceId = number 123                                  ERR_INVALID_SERVICE_ID; general message link

  3    Unauthorized change        Pull request that edits the number without a reviewer   Merge blocked (process test: branch protection and CODEOWNERS)

  4    Conflict or duplicate      Two services with the same id                           CI fails with ERR_DUPLICATE_SERVICE

  5    Dependency failure         Open the link on a phone without WhatsApp               Phone shows the WhatsApp page; Contact section still shows the number

  6    Response shape             Valid request                                           Result contains ok, link and service with the right types
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

