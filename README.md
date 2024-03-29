# oscal_authoring_demo
A repository to hold OSCAL content for demonstrations

# How is the ComplianceAsCode content transformed into an OSCAL Component Definition?


- The example control file used in this repository is [nist_ocp4](https://github.com/ComplianceAsCode/content/blob/master/controls/nist_ocp4.yml)
- One product equal one component and component definition - Example product we are using [ocp4](https://github.com/ComplianceAsCode/content/tree/master/products/ocp4)
- Upstream OSCAL [profiles](https://github.com/GSA/fedramp-automation/tree/master/dist/content/rev5/baselines) are being used to filter the controls that get included in the control implementation and as the control source in the control implementation on the component.

```mermaid
graph TD
    subgraph ComplianceAsCode
        subgraph ControlGroup
            subgraph Controls
                Status
                ParameterOverride
                ControlNotes(Control Notes)
                Rules
                Parameter
            end
        end
    end
    subgraph OSCAL Component Definitions
        ImplReq(Implemented Requirements)
        Statements
        subgraph Properties
        Description
            Remarks
        end
    end

    ControlNotes --> Status
    Status{Status Not Applicable?}
    Status -- Yes --> Remarks
    Status -- No --> ImplReq
    Status -- No --> Statements
    ParameterOverride{Parameter Defined in Control?}
    ParameterOverride -- Yes --> Description
    ParameterOverride -- No --> Parameter
    Rules --> Parameter
    Rules --> Description
    Parameter --> Description
```
