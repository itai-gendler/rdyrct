---
kind: configuration
of: capability-scenario
takesEffect: 'Fixed by the deployment: whether the instance has an email provider configured. It applies to every sign-up from then on.'
stability: Accounts created without a code stay unconfirmed; if the instance later sends email, they confirm with a code at their next sign-in.
alternatives:
- id: sign-up-with-verification-code
  selectedWhen: The instance has an email provider configured.
- id: sign-up-without-verification
  selectedWhen: The instance has no email provider configured.
---

# Sign-up verification

An instance with an email provider confirms every new address with a code before the first sign-in; a private instance without one lets people in straight away. Both are supported deployments.
