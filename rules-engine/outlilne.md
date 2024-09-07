This document is best viewed in vscode, which makes it possible to expand and collapse bullet points.

- RulesEngineResult
  - summary
  - balance point graph
  - array of normalized billing records
- BillingRecord
  - input => original inputed data 
    

- rules engine result - combin
- dhw input

File: engine.py
- **method** get_outputs_natural_gas(
    summary_input,dhw_input (optional)temperature_input,oil_propane_billing_input,
) 
  - Purpose: Entry method.  Given oil propane bill and other outputs, 
    returns a rules engine result (summary, balance point graph, and normalized billing records)
  - Flow:
    - creates a copy of oil_propane_billing_inut to an array of 
    normalized records.  Each item is of type NormalizedBillingPeriodRecordBase.
    - calls: passes the received parameters with normalized records replacing oil billing records and dhw_input as None
- Calls:
  - **get_outputs_normalized( **
    summary_input, dhw_input, temperature_input, billing_input,
  )
    - Purpose: Given normalized billing records and other inputs, 
      returns a rules engine result (summary, balance point graph, 
      and normalized billing records)
    - Flow: 
      - sets intermediate billing records equal to:
      **convert_to_intermediate_billing_periods** (summary_input, temperature_input, (normalized) billing_periods) which creates a set of BillingPeriod objects where billing_period.input equals the normalized billing record.
      - creates a home object and calculates info about home
      - derives average_indoor_temparate, average_heat_load, maximum_heat_load, summary_output, and balance_point_graph
    - Calls:
      - **convert_to_intermediate_billing_periods** (summary_input, temperature_input, billing_periods (normalized)) 
        - Purpose: For each (normalized) billing period object
          - input = (normalized) billing period
          - avg_temps = subset of temparature_inputs 
          - usage = billing_period.usage
          - analysis_type = derived from or equal to analysis_type
