Version: NAFATH-V2
Track: Software

## Overview
Providing reliable 5G services to emergency response teams presents a challenge that encompasses six technical domains. Software engineering supports efficient request processing, while artificial intelligence helps predict network congestion. Mobile application development enables response teams to access critical information during service outages and synchronize updates once connectivity is restored. Networking provides methods for managing data traffic and allocating resources for mission-critical communications. Cybersecurity assists teams in preparing for, detecting, and responding to attacks, as well as recovering affected services. Data engineering organizes service usage information, allowing teams to analyze performance across different regions and time periods. Together, these domains help network operators plan for congestion, service interruptions, and security incidents. The software section discusses secure and idempotent HTTP methods, highlighting their importance when clients automatically retry failed requests.

## Software
The GET method is considered safe and idempotent; it is designed to retrieve information without requesting changes to the server's state, and repeating the same request yields the same intended result as executing it once. While the PUT and DELETE methods are also idempotent, they are not considered safe because they may alter the server's state. This distinction is crucial when network issues cause request interruptions and force clients to resend them; understanding these methods helps developers minimize unintended consequences when requests are repeated.

Resource: RFC 9110: HTTP Semantics - https://www.rfc-editor.org/rfc/rfc9110.html

## AI
 "Overfitting" occurs when a machine learning model learns the training data with excessive precision, leading to poor performance when handling previously unseen data. "Cross-validation" helps assess a model's generalization capability by training and evaluating it using different subsets of the data. In the context of congestion prediction systems for 5G networks, this process helps identify models that may not perform efficiently outside the scope of their training data. However, cross-validation alone does not guarantee the required performance under all real-world network conditions; therefore, additional testing remains necessary before the system is actually deployed.

Resource: Techniques for Mitigating Overfitting in Machine Learning: A Comprehensive Review, Taxonomy, and Practical Guide - https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2026.1794271/full

## Mobile
Mobile applications that adopt an "offline-first" approach store critical data locally, enabling users to access it during network outages. Once connectivity is restored, local changes can be synchronized with the server. If synchronization fails, the application should retain the pending changes and allow for a retry. For emergency response teams, this approach helps safeguard critical field updates during periods of disconnection. Additionally, the application should clearly indicate instances where changes have not yet been synchronized, ensuring users are aware that the latest information may not be available on the server.

Resource: Offline Synchronization - https://docs.mendix.com/refguide10/mobile/building-efficient-mobile-apps/offlinefirst-data/synchronization/

## Networking
5G network slicing technology divides a shared physical network into multiple logical networks, each tailored to the requirements of specific services. A dedicated slice can be configured for emergency response teams to ensure reliable connectivity and low latency, even during peak periods. This helps critical data traffic secure the necessary network resources during times of congestion. However, a dedicated slice does not guarantee service continuity in every instance of an outage; therefore, network operators must actively monitor the network and develop contingency plans for potential failures.

Resource: 3GPP, Network Slicing - https://www.3gpp.org/technologies/network-slicing

## Cybersecurity
The incident response process helps organizations address cyberattacks through a structured approach. This process involves teams preparing before incidents occur, monitoring and analyzing suspicious activities, and then responding by containing the threat and eliminating its root causes. Subsequently, teams work to restore affected services and review the incident to enhance future readiness. In the context of emergency response services over 5G networks, these activities help minimize disruptions and restore critical communication services. Furthermore, response plans should be regularly tested and updated.

Resource: NIST SP 800-61 Rev. 3, Incident Response Recommendations and Considerations for Cybersecurity Risk Management - https://csrc.nist.gov/pubs/sp/800/61/r3/final

## Data
A star schema organizes data into a central fact table linked to dimension tables, such as those for date and region. A snowflake schema, by contrast, breaks down dimensions into related, normalized tables. For daily service usage reports broken down by region, a star schema is a suitable choice because its simpler structure facilitates data filtering, aggregation, and summarization. This can make creating and interpreting reports easier, though the optimal design ultimately depends on the specific requirements of the system.

Resource: Microsoft Learn, Understand star schema and the importance for Power BI - https://learn.microsoft.com/en-us/power-bi/guidance/star-schema

## Misconception in My Track
A common misconception in software engineering is the belief that software is reliable simply because it has passed initial tests. In reality, testing must continue throughout the entire development lifecycle and encompass a wide range of conditions, such as heavy workloads and unexpected failures. For 5G network services that support emergency response teams, periodic testing and robust error handling are critical to maintaining reliability under high-pressure conditions.

Resource: Google SRE, Testing for Reliability - https://sre.google/sre-book/testing-reliability/

## Open Question
How can software engineers design an emergency response service over 5G networks that remains reliable during periods of severe network congestion or partial network failure, while ensuring that emergency requests are neither lost nor processed more than once?

