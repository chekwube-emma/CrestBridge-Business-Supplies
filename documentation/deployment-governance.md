After developing the analytical model and report pages, I extended the project to include deployment and governance considerations within Power BI Service.

Row-Level Security
Row-Level Security was incorporated to demonstrate how access could be controlled for different users.
The objective was to ensure that users could view only the data relevant to their assigned scope, such as a particular branch or business area.
This introduced an important reporting-governance principle:
not every user should automatically have access to every level of organisational data.

Publishing to Power BI Service
The report was published from Power BI Desktop to Power BI Service.
This moved the solution from a local development environment into a shared reporting environment where it could support controlled access, refresh and distribution.

Gateway Configuration
Gateway configuration was included to understand how Power BI Service can connect to data sources that are not natively available in the cloud.
This demonstrated the operational steps required to maintain connectivity between the published report and its underlying data source.

Refresh Testing
Refresh testing was carried out to confirm that the report could update correctly when the underlying data changed.
This was important because a reporting solution is only useful if the information remains current.
The refresh process formed part of the wider reporting workflow:
Source Data → Transformation → Data Model → Report → Publish → Refresh → Updated Management Information

Governance Considerations
The project also incorporated several governance principles.
These included:
preserving the original source data;
separating raw data from transformed reporting data;
defining clear validation rules;
controlling which transactions contributed to financial KPIs;
maintaining structured dimension and fact tables;
applying access-control considerations;
testing report refresh behaviour.
These controls were designed to improve reliability, traceability and consistency within the reporting process.
Governance Principle
The project reinforced that business intelligence is not only about creating dashboards.
A reliable reporting solution also requires attention to:
Data Quality → Business Rules → Access Control → Refresh → Consistency → Traceability
This helps ensure that decision-makers are not only receiving attractive reports, but information they can trust.
