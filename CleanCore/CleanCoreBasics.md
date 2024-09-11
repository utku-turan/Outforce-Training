# Clean Core for SAP S/4HANA Cloud - Basics
My notes from the SAP Training [Managing Clean Core for SAP S/4HANA Cloud](https://learning.sap.com/learning-journeys/managing-clean-core-for-sap-s-4hana-cloud) 

Traditionally, companies hosted and managed SAP's ERP systems within their own data centers. However, with the introduction of cloud-based ERP systems like SAP S/4HANA Cloud, updates are delivered continuously.

This continuous update model necessitates a different strategy for managing extensions and integrations compared to the traditional on-premise environment. To address this, SAP introduced the "clean core" concept, which customers can adopt to optimize the performance and efficiency of SAP S/4HANA Cloud.

SAP S/4HANA Cloud offers a robust platform for customers to leverage technological advancements. Since it's a cloud-based ERP, SAP handles all updates, reducing the need for extensive IT resources and minimizing business disruptions.

The system comes with integrated security, compliance, and scalability, ensuring that essential operations like backups, disaster recovery, system maintenance, and data protection are automatically managed, providing customers with peace of mind.

Customers can take advantage of SAP S/4HANA Cloud's built-in features, including automated updates, cloud-native architecture, and inherent compliance and scalability.

## Why A Clean Core Is Necessary
- **Business Change:** Disruption of supply chains, Changing customer preferences, Regulatory compliance.
- **New Technologies:** Embrace new technological advancements, accelerate innovation, optimize and automate business processes, and foster agility (ability to pivot quickly).
- **Landscape Compexity:** Business model adaptations, Key application adjustments, Changing customer preferences, Cloud Computing and Agile Development, SAP S/4HANA Cloud and SAP BTP.

## Clean Core Components
Clean Core Dimensions:
- Processes
- Extensions
- Data
- Integrations
- Operations

When we refer to "Clean," it means that for each of the dimensions mentioned, there is a specific set of best practices, methodologies, and tools available. By following these, customers can ensure that the respective dimension is considered "clean." Each dimension has its own tailored best practices, methodologies, and tools designed to achieve this.

In the ideal scenario for a clean core, the system is fully up-to-date with the latest release, features cloud-compliant extensions and integrations, maintains high-quality master data, and has flawlessly designed processes.

By definition, a newly provisioned SAP S/4HANA Cloud system is clean. The customer's objective, therefore, is to maintain this clean core over time.

For customers opting for a system conversion or system landscape transformation, the primary goal is to to get (and then keep) the core clean.

Some key characteristics of a clean core include:
- A streamlined and optimized version of SAP S/4HANA Cloud, focusing exclusively on essential functionalities to deliver maximum efficiency.
- Elimination of unnecessary features, customizations, and complexities to simplify the ERP system's core codebase.
- Improved maintainability, reduced technical debt, and enhanced overall system performance.

### Features of Clean Core components
- **Minimalism:** Focuses on simplicity by removing redundant or obsolete functionalities, leaving only essential components.
- **Modularity:** Supports breaking down the ERP system into loosely coupled modules, making maintenance and adaptation easier.
- **Scalability:** Enables the system to grow and evolve without compromising performance or stability.
- **Maintainability:** Simplifies the codebase, making it easier for developers to understand, modify, and enhance the system.
- **Stability and Reliability:** Enhances stability by reducing dependencies, minimizing bugs, and improving overall system reliability.

### Results after achieving a Clean Core:
- **Improved Performance:** Optimization and minimalism lead to faster system response times and greater user satisfaction in the now clean ERP.
- **Simplified Development:** Developers benefit from a streamlined codebase, leading to better productivity and shorter development cycles.
- **Enhanced Stability and Reliability:** Eliminating unnecessary complexities reduces the likelihood of bugs and errors, making the ERP system more reliable and stable.
- **Cost Reduction:** The clean core decreases maintenance efforts, resulting in less downtime and lower overall maintenance costs.

### Key points for a Clean Core implementation:
- **Thorough Business Analysis:** Start by conducting a comprehensive business analysis to identify critical functionalities before initiating clean core development.
- **Modular Development:** Utilize modular development frameworks and practices to ensure loose coupling and scalability.
- **Continuous Performance Review:** Regularly assess the ERP system's performance to identify opportunities for further optimization and code cleanup.
- **Stakeholder Involvement:** Engage stakeholders from various departments to ensure alignment with business goals and requirements.

### Misconceptions about Clean Core
- **SAP BTP is the Only Way to Maintain a Clean Core:** While SAP BTP is essential for creating side-by-side extensions (a key aspect of clean core), SAP S/4HANA Cloud also supports both key user and developer extensibility, allowing for clean core management within the stack.
- **Clean Core is Only About Custom Code and Extensibility:** Clean core encompasses more than just custom code and extensions; it also impacts business processes, data management, integrations, and operational practices.
- **Clean Core is Only About Total Cost of Ownership (TCO):** Although clean core helps reduce TCO, its benefits extend beyond cost savings. It also facilitates access to the latest innovations and supports a shift from on-premise to cloud-based solutions.
- **Fit-to-Standard is the Only Way to Achieve a Clean Core:** While adhering to fit-to-standard practices can lead to a clean core, the use of Tier 1 extensibility options (which will be covered in a later lesson) can also contribute to maintaining a clean core.

### Implementation Types and Clean Core
- **Greenfield (New Implementation):** Adopting the greenfield approach enables a fresh start, allowing for a clean core from the outset. This method ensures greater efficiency and minimizes complexity, as the new system is inherently clean by default.
- **Brownfield (System Conversion):** The target SAP S/4HANA Cloud instance (whether private edition or on-premise) retains some complexities from the previous system, which can be challenging. This approach means inheriting historical complexities and possibly unwanted customizations. Despite these challenges, a clean core can still be achieved through system conversions. While the system doesn’t start clean, the goal is to systematically make it clean. To implement a clean core in this scenario, you must identify which elements of the legacy system to retain, eliminate, or transform. This requires a deep understanding of the current system's functions and a clear plan for how SAP S/4HANA Cloud can facilitate the desired changes. The process involves efficiently reconciling old and new elements—transforming and adapting aspects like custom code—to ensure compliance with the clean core principles of SAP S/4HANA.

When deciding between a greenfield or brownfield approach, several factors come into play, with business processes being a crucial consideration.
- If the client is ready and capable of adopting new business processes aligned with current best practices through a fit-to-standard approach, a greenfield strategy is a viable option. This approach allows them to implement a clean core from the start, free from the constraints of legacy coding and design.
- If the existing system involves complex business processes that are essential and would be costly or difficult to redesign from scratch, a brownfield approach may be more suitable. While a clean core remains the goal, this approach allows for the preservation of critical business processes while working to achieve a clean core.

Applying clean core principles in migrating to SAP S/4HANA Cloud involves balancing business requirements with implementation strategies. As developers, our role extends beyond coding; we serve as crucial intermediaries in ensuring that the upgraded system aligns with business needs while adhering to clean core principles.

A greenfield approach offers the most straightforward path to achieving a clean core but may not always be feasible. On the other hand, a brownfield approach, while accommodating specific business complexities, still allows for the transformation and simplification of existing code to comply with clean core standards.

The decision between greenfield and brownfield strategies closely depends on the business context, available resources, and willingness to embrace extensive changes. Understanding the implications of these strategies on clean core principles helps us make informed decisions that best serve the business.

## Benefits of Clean Core
### Benefits of Clean Core for Users
- **Performance:**  improved system performance and responsiveness
- **Cleansed Data:** clean data ensures data integrity and accuracy, which is crucial for informed decision-making.
- **System Reliability:** release management is established as a foundation and is integrated in day-to-day operations for the system.
- **Business Process Flexibility:** can adapt to changing conditions whether those changes originate from regulatory oversight, the market, or any other reason.

Clean core enhances users' ability to make quicker, more informed decisions by improving data quality and availability.

Challenges created by the legacy systems:
- Data silos and inefficient communication
- Manual and time-consuming processes
- Lack of real-time insights

### Benefits of Clean Core for IT
- **Software Stack:** With SAP S/4HANA Cloud and SAP Business Technology Platform, you no longer need to manage the core software stack. Both platforms are continuously updated to the latest release automatically, eliminating the need for you to implement upgrades or maintenance packs yourself. You also have access to a wide range of partner solutions that are clean core compliant. Additionally, you can consider these solutions or opt to build side-by-side extensions using SAP Business Technology Platform if needed.
- **Business Process Flexibility:** All stakeholders, including management, have agreed to implement SAP Best Practices content with SAP S/4HANA Cloud.
- **Cloud Native Development:** You benefit from an end-to-end cloud-native development model (ABAP Cloud Development Model) and an end-to-end extensibility model (SAP S/4HANA Cloud Extensibility Model). These frameworks enable you to develop extensions while preserving a clean core. With this approach, modifications are no longer necessary, and upgrades do not disrupt extensions, nor do extensions interfere with upgrades.
- A clean core improves IT strategy and execution now and sets the foundation for the future.

### Benefits of Clean Core for the Company
- **Streamlined Operations:** By integrating all departments and processes into a single, centralized system, you can eliminate duplicated efforts and minimized delays caused by manual data entry. This results in streamlined workflows, reduced paperwork, and quicker response times.
- **Cost Savings:** With the ERP system in place, you gain real-time visibility into your inventory levels, ensuring optimal stock levels and reducing the risk of stockouts. Automated inventory tracking, combined with data analytics, allow you to identify trends, predict demand fluctuations, and make informed purchasing decisions. This can lead to a significant reduction in inventory holding costs and higher customer satisfaction through improved order fulfillment rates.
- **Improved Decision Making:** One of the key strengths of SAP S/4HANA Cloud is its ability to generate real-time reports and offer in-depth insights into various business operations. With access to accurate, up-to-date information, your company management can gain a comprehensive view of the entire production process, allowing for faster, more informed decision-making. Additionally, the system's customizable dashboards and reporting tools enables intuitive visualizations, trend analysis, and forecasting. These features empower your company to identify market trends, optimize processes, and align production strategies with customer demands effectively.
- **Enhanced Collaboration:** Instead of relying on fragmented communication channels or inconsistent spreadsheets, employees gain access to a centralized platform for information sharing. This improves communication, reduces errors, and enhances coordination throughout the production process.

## Dimensions of Clean Core
### How to Make Business Processes Clean Core Compliant
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

### How to Make Extensions Clean Core Compliant
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

### How to Make Data Core Compliant
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

### How to Make Landscapes Core Compliant
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
- **Apply SAP Integration Suite:** 
