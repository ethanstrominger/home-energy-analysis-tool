This document is best viewed in vscode, which makes it possible to expand and collapse bullet points.

- get_outputs_natural_gas(
    summary_input,dhw_input (optional)temperature_input,oil_propane_billing_input,
) 
  - Purpose: Entry method.  Given oil propane bill and other outputs, 
    outputs a summary and analytic data about each bill to screen.
  - Flow:
    - creates a copy of oil_propane_billing_inut to an array of 
    normalized records.  Each item is of type NormalizedBillingPeriodRecordBase.
    - calls: passes the received parameters with normalized records replacing
      oil billing records.
- Calls:
  - get_outputs_normalized(
    summary_input,dhw_input (optional)temperature_input, billing_input,
  ) 
    - Purpose: Given normalized billing records and other inputs, 
    outputs a summary and analytic data about each bill to screen.
