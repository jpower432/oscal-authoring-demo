# oscal_authoring_demo
A repository to hold OSCAL content for demonstrations

# How is the ComplianceAsCode content transformed into an OSCAL Component Definition?


- The example control file used in this repository is [nist_ocp4](https://github.com/ComplianceAsCode/content/blob/master/controls/nist_ocp4.yml)

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