# Dimensions of Clean Core
## How to Make Business Processes Clean Core Compliant
- **Establish Organizational Structure, Technical Foundation, and Transformation Methodology:** Establishing a strong organizational structure means defining clear roles and responsibilities. Building a robust technical foundation involves selecting the correct tools and technologies to support the business processes, as well as ensuring that the infrastructure is scalable and secure. SAP S/4HANA Cloud along with SAP BTP to along with other tools fulfill this requirement. Having a transformation methodology in place, based on the different types of project implementation approaches, involves having a clear, repeatable process for evaluating, implementing, and optimizing business processes.
  - Project teams can use the following as a guidepost:
    - Define roles and responsibilities as part of a process transformation office (or similar instance driving the success of business process transformation).
    - Set up an end-to-end toolchain connecting Enterprise Architecture Management with Business Process Management and Application Lifecycle Management.
    - Establish guidelines for governing process enhancements and improvements.
  - Key solution capabilities to help project teams:
    - LeanIX: LeanIX solutions allow teams to visualize their IT application landscape, identify outdated applications, design a target state, and plan new architectural roadmaps.
    - SAP Solution Manager and SAP Cloud ALM: Both tools help accelerate time-to-value and reduce TCO. SAP Cloud ALM, a cloud-native solution, supports the implementation and operation of SAP Cloud and hybrid landscapes.
    - SAP Signavio Process Manager: An intuitive and comprehensive platform for business process management (BPM), enabling organizations to rapidly capture, improve, and maintain business processes at scale.
    - SAP Signavio Process Governance: Converts business process models from Process Manager into standardized workflows, helping organizations enhance internal and external compliance through effective process governance.

- **Setting Up a Prioritized Business Process Hierarchy:** This involves identifying and categorizing core business processes based on their strategic importance, regulatory requirements, and impact on business operations. By prioritizing these processes, organizations can focus their efforts on optimizing the critical aspects of their business, leading to better outcomes and reduced compliance risk.
  - The next step is to segment the business process views into end-to-end and functional perspectives. End-to-end process views provide an overall understanding of how data flows through the organization. Functional process views focus on the specific activities and tasks within each business function. By segmenting the business process views, organizations can gain a comprehensive understanding of their operations and identify opportunities for improvement and optimization.
  - Project teams can use the following as a guidepost:
    - Identify end-to-end processes and journeys based on corporate strategy and goals, identify and cluster functional processes into different layers. For example, commodity, differentiating, and innovating.
    - Prioritization and segmentation of E2E and functional processes (optionally, apply pace layers from capability maps in EAM tool).
  - Key solution capabilities provided by SAP Signavio to help project teams:
    - SAP Signavio Process Insights
    - SAP Signavio Process Intelligence

- **Align To-be Process Design and Technical Realization:** by applying best practices and centrally governing the to-be process, business requirements, and design approvals. By adopting and adapting these best practices to your own business, you can significantly improve the efficiency and effectiveness of your processes while reducing the need for complex customizations.
  - Centrally governing the to-be process, business requirements, and design approvals can be accomplished by establishing a central authority or team to oversee the design and implementation of business processes in SAP ERP. By doing so, you can ensure that all processes are aligned with best practices, meet business requirements, and are approved in a standardized and consistent manner.
  - Guidepost for project teams:
    - Analyze Current Processes: Evaluate as-is process execution to identify areas for potential improvement.
    - Use Best Practices: Leverage preconfigured best practice content as a foundation for designing future processes.
    - Centrally Govern Process Design: Manage to-be process design and related business requirements in a centralized platform.
    - Align Solution Design with Processes: Connect solution design, testing, realization, and rollout with the predefined to-be process for seamless execution.
  - Key solution capabilities to help project teams:
    - Methodology for SAP S/4HANA implementation: SAP Activate.
    - General Guidance on SAP S/4HANA implementations and Best Practices.
    - Preconfigured best practice processes, ready to consume: SAP Signavio Process Explorer, including, for example Enterprise Management Layer for SAP S/4HANA).
    - Business process and journey modeling: SAP Signavio Process Manager.
    - Workflow engine to turn business process models into executable workflows: SAP Signavio Process Governance.
    - Continuous commenting and collaboration on business processes: SAP Signavio Process Collaboration Hub.

## How to Make Extensions Clean Core Compliant
- **Decouple Extensions from Standard:** Adhering to clean core extensibility principles preserves system integrity, boosts efficiency, and enables seamless upgrades.
- **Extensions Must Be Avoided When Possible:** Once business processes are clean core-compliant, it's straightforward to assess whether SAP S/4HANA Cloud’s out-of-the-box functionality can support them. If not, custom development or extensions may be required. However, by minimizing extensions, you can reduce system complexity and maintenance overhead, ensuring a more streamlined and efficient ERP system. Further to this requirement, to approve extensions, companies must set up a clean governance structure with high demands. The documentation of why the extension was needed must be clear, and so must the proposed value of the extension.
- **Extensions Don't Break Upgrades And Upgrades Don't Break Extensions:** To prevent extensions from disrupting upgrades (or vice versa), extensions must be kept separate from SAP S/4HANA Cloud's core code. The SAP S/4HANA Cloud extensibility model was designed specifically for this purpose, ensuring that extensions do not interfere with SAP's continuous updates and innovations.

- The model is built around the following **key principles:**
  - Extensions can be implemented either internally within SAP S/4HANA Cloud as on-stack extensions, or externally as side-by-side extensions on SAP Business Technology Platform.
  - Extensions must use only released local or remote public SAP Application Programming Interfaces (APIs), BAdIs, and ABAP RESTful Application Programming Model Business Object (BO) extension points.
  - Extensions must be developed using cloud-enabled and officially released technologies.

- Regarding the first principle, there are **three types of extensions**, categorized into two groups:
  - **On-stack extensions (within SAP S/4HANA Cloud):**
    - **Key user extensions (type 1):** These are created by business users with no need for deep technical expertise, allowing modifications like UI adaptations or simple logic changes.
    - **Developer extensions (type 2):** Created by developers, these extensions involve more complex changes, including custom business logic or deeper system modifications.
  - **Side-by-side extensions (type 3):** These are developed externally on SAP Business Technology Platform, allowing for more advanced and flexible functionality without altering the core SAP S/4HANA Cloud system.

- Generally, type 1 or type 2 extensions are created when close coupling to SAP S/4HANA Cloud is necessary. Type 3 extensions are created when a looser coupling is acceptable.
- Closely related to the first principle, clean core extensibility requires the use of "released" APIs and extension points (BAdIs or BO extension points). Non released objects cannot be used.
- Both principles, when taken together, provide complete transparency (a clear separation) regarding customer code versus SAP code.

- **Extensions Must Be Cloud Compliant:** The third principle of the SAP S/4HANA Cloud development model is the use of cloud-enabled and released technologies. The two main guideposts for customers to implement this principle are:
  - ABAP Cloud Development Model
  - Three-Tier Extensibility Model

- **ABAP Cloud Development Model:** SAP developed the ABAP Cloud development model (ABAP Cloud) to address the needs of cloud-native development. It is an evolution of classical ABAP, preserving the familiar features and benefits of the ABAP language while removing elements that are incompatible with SAP S/4HANA Cloud.
  - In summary, ABAP Cloud is structured around the following principles:
    - Only approved ABAP Cloud object types (such as ABAP RESTful application programming model artifacts) can be created.
    - ABAP Cloud language is enforced through syntax checks.
    - The use of released APIs is also enforced via syntax checks.
    - All development objects are created using ABAP development tools for Eclipse.

- **Three Tier Extensibility Model:** to accommodate different customer needs at different stages of their cloud journey. (public, private, on-premise)
  - ***Tier 1*** is mandatory for public edition customers and recommended for private edition customers. It is also recommended for on premise customers, especially if they plan to move to public or private edition in future, as artifacts developed in accordance with Tier 1 principles will smoothly migrate with minimal disruption. It means that extensions are exclusively developed using ABAP Cloud and the SAP S/4HANA Cloud extensibility model. Classic ABAP and classical extensions are not supported.
  - ***Tier 2*** was created for customers adopting private edition / on premise. For those customers, there may be an object (a function module for example ) that has not yet been "released" by SAP but is still necessary for successful extension development. The unreleased object is "wrapped" by a released object (for example, a released ABAP class in one of its methods, calls an unreleased ABAP function module). Since the wrapping object is released, the rules of ABAP Cloud are satisfied (only released APIs can be used). Customers can use the Customer Influence Tool to ask SAP to release APIs. When the API is released by SAP, the wrapper can be removed.
  - Build cloud-compliant extensions, which are integrated via stable interfaces. Extensions must never duplicate SAP S/4HANA Cloud standard functionality.

- **Precisely Understand the Requirement Before Extending:** If extensions are required, project teams must carefully evaluate how to implement them and anticipate future needs. This involves two key considerations. First, it is essential to decide whether to develop the extension as an on-stack or side-by-side extension, following the SAP S/4HANA Cloud extensibility model. Second, for private edition and on-premise customers, it must be determined whether to use classical extension techniques. These classical extensions form the ***third "tier"*** of the three-tier extensibility model. However, they are discouraged due to the high risk of disruption during system upgrades and the certainty of disruption if the customer transitions to the public edition. Nevertheless, if Tier 1 or Tier 2 approaches are not viable, classical extensions can be used, provided the customer understands the associated risks. Classical extensions represent ***Tier 3*** in the extensibility model.
  - To help with this decision, customers can use the SAP Application Extension Methodology. This methodology allows customers to assess their extension use cases and define an extension target solution in a structured and formalized way.

## How to Make Data Core Compliant
- **Control Data According to Latest Standards:** "Keep the data clean". Data efficiency is only as good as the core principles governing its cleanliness. SAP S/4HANA Cloud system stores three types of data: Configuration, Master, Transactional.

- **Data Quality:**
  - **Accuracy:** Data accurately reflects the reality of the business. To maintain accuracy, it's essential to implement data validation rules, perform regular data quality checks, and establish data governance processes to address any issues that may arise.
  - **Completeness:** Define data requirements and ensure that all relevant data is captured and maintained. This may involve establishing data collection processes, implementing data entry validation, and enforcing data entry standards to prevent incomplete data from entering the system.
  - **Consistency:** Establishing data standards and guidelines, conducting data profiling and cleansing activities, and implementing data integration and reconciliation processes are essential for maintaining data consistency.
  - **Timeliness:** Implementing real-time data capture and integration processes, defining data refresh and update schedules, and setting up data monitoring and alerting mechanisms are essential for ensuring timely and up-to-date data.
  - **Validity:** Validity ensures that the data conforms to defined standards and business rules, and that it accurately represents the real-world scenario it purports to capture.
  - **Uniqueness:** Implementing data validation checks, enforcing data integrity constraints, and using data duplication and matching tools are essential for maintaining validity and uniqueness in your data.

- **Achieving Data Quality:**
  - ***SAP Master Data Governance*** provides a central hub for master data management and governance. With it customers can create a single source of truth by uniting SAP and third party data sources.
  - Customers can also use ***SAP Information Steward*** to understand, analyze, and quantify the impact of data on their business processes to enhance operational, analytical, and data governance initiatives.
  - ***SAP Datasphere*** is also available and is a comprehensive solution providing data capabilities such as integrating, cataloging, semantic modeling, data warehousing and virtualization.
  - Finally, customers are encouraged to adhere to the ***SAP One Domain Model (ODM)***. This model defines a common, harmonized data model to facilitate data exchange and reuse between business applications of the Intelligent Suite and its ecosystem.
  - They are also encouraged to use the ***SAP Data and Analytics Advisory Methodology*** the purpose of which is to provide guidance in the design and validation of solution architectures for data-driven business innovations.

- **Data Volume Efficiency (From Creation to Retirement):** One major step towards becoming clean core data compliant involves removing redundant, outdated, or unused data. It's a straightforward concept, but it's essential in maintaining the usefulness and relevance of the database. Data has a shelf life. Regular data audits can help identify and eliminate such unnecessary information.
- **Data Privacy Compliance:** It's crucial that personal master data be stored only when necessary and for justifiable purposes. Collecting unnecessary personal data may lead to misuse or unintended breaches, damaging trust, and potentially bringing legal repercussions. It's essential to respect user rights, collect only data required for operational needs, and maintain transparency about data usage.
  - Data privacy compliance is best addressed through ***SAP Information Lifecycle Management*** which allows the automation of data archiving and retention, as well as the decommissioning of legacy systems, while balancing the total cost of ownership, risk, and legal compliance.

- **Benefits of Clean Data:**  "Data To Value" (defined as the reliability of results when using data in processes and applications) is achieved. Also stability and quality of business process steps (business process efficiency) along with reduced TCO due to efficient data volume management becomes possible. Finally, the improved ability to exchange data between different solutions paired with a lower risk of breaching data privacy protection regulations can be accomplished.

- Goals for data: Complete, Correct, Used and relevant

## How to Make Landscapes Core Compliant
- Making SAP S/4HANA Cloud integrations clean core compliant is essential for organizations looking to optimize their ERP environment.
- Organizations can streamline their integration processes and ensure clean core compliance by following best practices and using appropriate tools, such as:
  - OData API's.
  - SOAP API's.
  - SAP Integration Suite.
  - SAP Event Mesh.
  - SAP Application Interface Framework.
- Goals:
  - Upgrade stable interfaces.
  - Proper monitoring and error resolution capabilities
  - Only actively used and well-documented integration

- **Base Integrations on Standard APIs:** base the integrations as much as possible on standardized OData and Simple Object Access Protocol (SOAP) APIs. These APIs allow for communication and data exchange between systems, ensuring smooth and efficient processes. An excellent tool to discover and explore APIs is the ***SAP Business Accelerator Hub***. With this tool, customers can explore APIs by category, product, domain, or even business process. In addition to basic exploration, for OData APIs customers can "try them out" against a sandbox system provisioned by SAP and dedicated for this purpose.
- **Apply SAP Integration Suite:** is SAP's integration platform as a service (iPaaS). It determines whether incoming messages need to be routed to the target system (routing). If required, it performs message mapping to modify the message before forwarding it (mapping). It leverages a comprehensive set of adapters to ensure the message is in a format compatible with the target system (connectivity). Both the OData and SOAP adapters allow developers to quickly and easily establish connectivity with target systems. Integration scenarios can be set up, and importantly, easily tested.
- **Use SAP Event Mesh for Event-Based Scenarios:** SAP Event Mesh, a service offered as part of SAP Business Technology Platform, enables applications to communicate through asynchronous events. This communication method supports the design of event-driven business processes. In an event-driven architecture, an event provider triggers an event, and an event consumer is notified and responds accordingly. SAP Event Mesh acts as the "glue" that connects the event provider and consumer, facilitating seamless interaction between them. These "asynchronous" designs are suitable for certain types of integration scenarios. The SAP Business Accelerator Hub, as with standardized OData and SOAP APIs, offers customers the ease and convenience of exploring event objects that can be used in integration scenarios.
  - For example, a company maintains business partners using SAP Master Data Governance on SAP S/4HANA Cloud and a business partner's mailing address is changed (a "change of state"). An event is raised. Both the event itself and also (if necessary) some contextual data associated with it is transferred to SAP Event Mesh. Several custom-built applications (such as a Node.js application running in SAP BTP, Cloud Foundry runtime) have "subscribed" to this event. SAP Event Mesh notifies them of the event and the contextual data. The custom-built applications then respond to the event. For example, each application can request the updated business partner information from SAP S/4HANA Cloud or an application can kick off a notification workflow for interested stakeholders.
- **Avoid Legacy APIs And Their Legacy Extension Options:** While Remote Function Call (RFC) and Intermediate Document (IDoc) are commonly used in SAP systems, they should only be considered for integrations when absolutely necessary. These older technologies do not align with clean core principles, which emphasize reliability and flexibility in integration. It is preferable to use newer, more adaptable technologies like OData and SOAP for integrations. By avoiding RFCs and IDocs, organizations can adopt modern integration approaches that better support clean core principles, fostering a more agile and efficient ERP environment.
- **Use SAP Application Interface Framework:** It enables business users to centrally monitor interfaces across various technologies, such as OData and SOAP, set up alerts for errors, and resolve issues without needing IT support. Security features ensure that sensitive data not required for monitoring or error resolution is hidden from business users. SAP Application Interface Framework helps companies streamline their landscapes, reduce error-handling time, and enhance governance across their system landscapes.
- **SAP Integration Solution Advisory Methodology:** ISA-M offers a comprehensive framework that helps accelerate hybrid integration platform design, safeguard integration projects based on SAP best practices, and enable an agile integration practice across your organization. Based on the methodology, companies can define, document, and apply a strategy for enterprise.
  - The methodology offers a framework that includes:
    - Integration use case patterns
    - Architecture blueprints
    - More best practices for cloud and hybrid IT landscapes
  - Its scope extends beyond technical aspects to include the organizational dimension of enterprise integration, such as establishing an Integration Center of Excellence and defining integration roles along with their responsibilities. This open framework can be applied to both SAP integration technologies and those from other vendors. It is also adaptable, allowing you to customize and enhance its concepts and content to meet your specific needs. A clear adoption path is provided, enabling you to implement the methodology in your organization step by step.
  - Customers are encouraged to use ISA-M to establish a clean core-compliant integration strategy. The easiest way to do so is through SAP Integration Assessment. SAP Integration Assessment is included in SAP Integration Suite and is also available as a separate service running in the SAP Business Technology Platform, Cloud Foundry environment. It applies SAP Integration Solution Advisory Methodology in a tool-based way.

## How to Make Operations Core Compliant
- **Keep the Operations Effective and Efficient:**
  - Day-to-day operations are planned and applied regularly.
  - Opt-in on lifecycle events such as periodic upgrades
  - Compliance with preapproved maintenance windows

- **Clean Core Must Be Integrated in the End-to-End Value Process Chain for Operations:** Governance frameworks, strategic and tactical decision-making and even day-to-day decisions must always be designed and applied with clean core in mind.
  - IT must set up integrated monitoring and alerting for all aspects of the clean core, including data and extensions. This integrated view enhances control and management. IT, in collaboration with all stakeholders, should also establish procedures for event management and escalations, ensuring that these procedures align with clean core governance models.
  - There are two tools that are highly effective in achieving this goal, SAP Solution Manager and SAP Cloud Application Lifecycle Management (SAP Cloud ALM).
  - **SAP Cloud ALM** is itself a newer cloud native designed solution built entirely on cloud technology. It is included automatically in all cloud subscriptions, ready to use. Here are some of SAP Cloud ALM's features that support clean operations:
    - Detect if any incidents have occurred.
    - Analyze the root-cause of incidents.
    - Correct the identified problem.
    - Automate recurring activities.

- **Release Management Is an Established Foundation for Clean Core:** System to always be at the latest release. For SAP S/4HANA Cloud Public Edition customers, updates are not an issue, as they are automatically pushed to all customers simultaneously. However, for customers using SAP S/4HANA Cloud Private Edition or SAP S/4HANA on-prem, automatic updates are not enforced. These customers can implement product-based innovations according to their own timeline. Still, it is essential that they aim to stay on the latest release, and if not, they must have a clear rationale for the delay. A defined timeline for adopting new releases must be established, as SAP S/4HANA should not remain "frozen." This timeline should be explicitly documented in governance frameworks, with exceptions permitted only for extraordinary reasons.
  - **Regular Housekeeping Tasks and Procedures Are Established:** Exactly which tasks and procedures vary from company to company.
    - Designing Background Jobs for Efficient Use of Infrastructure rather than creating unnecessary system loads.
    - Avoiding File Interfaces for Data Import or Export
    - Regular Reviewing and Adapting User Authorizations

- **Clean Core Dashboard:** To support clean core operations, customers can utilize the clean core dashboard. Through the Clean Core Compliance tab, users can access key clean core metrics. These metrics include the software stack version, the number of custom code objects, the volume of business modifications, and the Tier 1 extensions implemented.
  - Things to note about the clean core dashboard:
    - The dashboard is only available for SAP S/4HANA Cloud Private Edition systems.
    - Customers can grant access to the dashboard to partners.
    - Metrics are collected for productive systems only.
    - Two authorizations are needed to access the dashboard: (1): SC_CCCREAD + (2): INSTDISP (read) or INSTPROD (edit).
    - The main channel for collecting dashboard data is Early Watch Alert (EWA), which SAP will set up.
