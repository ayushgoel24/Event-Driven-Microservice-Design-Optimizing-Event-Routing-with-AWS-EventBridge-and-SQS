# Event-Driven Microservice Design: Optimizing Event Routing with AWS EventBridge and SQS

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![GitHub Issues](https://img.shields.io/github/issues/ayushgoel24/Event-Driven-Microservice-Design-Optimizing-Event-Routing-with-AWS-EventBridge-and-SQS.svg)](https://github.com/ayushgoel24/Event-Driven-Microservice-Design-Optimizing-Event-Routing-with-AWS-EventBridge-and-SQS/issues)
[![Contributions welcome](https://img.shields.io/badge/Contributions-welcome-orange.svg)](https://github.com/ayushgoel24/Event-Driven-Microservice-Design-Optimizing-Event-Routing-with-AWS-EventBridge-and-SQS)

<p style="text-align: justify">This repository provides an architectural outline of an innovative, event-driven microservice model that maximizes efficiency by using AWS EventBridge and SQS. While the core code is proprietary, the insights and design principles can serve as a blueprint for similar implementations.</p>

## Table of Contents
1. [Overview](#overview)
2. [Architecture](#architecture)
3. [Results](#results)
4. [Key Achievements](#key-achievements)
5. [Benefits](#benefits)
6. [Impact](#impact)
7. [Conclusion](#conclusion)

## Overview:
<p style="text-align: justify"> In the complex landscape of e-commerce, our project embraced a sophisticated event-driven microservice architecture, utilizing the power of AWS EventBridge and SQS to streamline the dynamic challenges of efficiently routing, handling, and processing a vast influx of diverse state change events. These events, which encapsulate vital data regarding orders, inventories, and returns, originate from a myriad of downstream systems operating across different sellers and marketplaces. By implementing a decoupled system design, the architecture ensured scalability and resilience. Redundant API calls were dramatically reduced, optimizing system throughput and latency. Additionally, with the integration of AWS CloudWatch, we achieved granular monitoring and alerting capabilities, ensuring that the system's health and performance were consistently at their peak. This holistic approach resulted in a robust, agile, and scalable system design that catered to the ever-evolving demands of modern e-commerce platforms. </p>


## Architecture

<p style="text-align: justify"> The project's architecture is designed to ensure efficient event processing, resilience, and scalability. Here's a detailed breakdown:</p>

1. <p style="text-align: justify"><b>Event Producers</b>: Multiple downstream systems consistently push state change events, including updates related to orders, inventories, and returns for different e-commerce marketplaces and sellers.</p>

2. <p style="text-align: justify"><b>AWS EventBridge</b>: Positioned as the central hub, EventBridge seamlessly intercepts these events. Using predefined rules, it routes these events to the appropriate SQS queues, ensuring that every event reaches its intended destination.</p>

3. <p style="text-align: justify"><b>SQS Queues</b>: Serving as temporary storage and processing endpoints, these queues hold routed events until they are consumed. They guarantee that no event is lost and are designed for concurrent processing, facilitating timely event handling.</p>

4. <p style="text-align: justify"><b>SQS Consumers</b>: Distributed systems designed to process or consume events from the SQS queues. They're scalable and can be ramped up to handle high event loads, ensuring events don't languish in the queue for extended periods.</p>

5. <p style="text-align: justify"><b>Dead Letter Queue (DLQ)</b>: An essential component in our fault-tolerant design, the DLQ handles events that can't be processed after several attempts. This ensures that problematic events are isolated, examined, and dealt with, without stalling the processing of other events in the main queues.</p>

6. <p style="text-align: justify"><b>Repushing Mechanism</b>: For events that may experience temporary processing failures, our architecture has a mechanism to repush them back into the SQS queues. This ensures that transient issues don't result in event loss, and every event gets a fair chance at processing.</p>

7. <p style="text-align: justify"><b>Monitoring with CloudWatch</b>: CloudWatch provides continuous surveillance over every component of the architecture. From monitoring the health and length of SQS queues to the activity of consumers and the DLQ, CloudWatch offers insights and proactive alerts for optimal system performance.</p>

<p style="text-align: justify">This architecture, with its decoupled design, ensures that the system remains resilient to failures, scalable to handle event spikes, and efficient in processing each event in a timely manner.</p>

## Results
The integration with AWS EventBridge and SQS has delivered tangible results:
- **Reduced API Calls**: Witnessed a 25% reduction in unnecessary API calls.
- **System Efficiency**: Achieved a 30% increase in overall system efficiency.

## Key Achievements
- <p style="text-align: justify"><b>Enhanced System Efficiency</b>: The introduction of AWS EventBridge led to a remarkable 25% reduction in API calls, optimizing the system efficiency by 30%.</p>

- <p style="text-align: justify"><b>Real-time Monitoring</b>: AWS CloudWatch metrics were incorporated for real-time monitoring, ensuring rapid responses to critical system events.</p>

## Benefits
- <p style="text-align: justify"><b>Scalability</b>: The architecture's event-driven nature ensures seamless scalability, accommodating increased event loads.</p>

- <p style="text-align: justify"><b>Resilience</b>: With inherent retry mechanisms and a decoupled design, the system is robust and less prone to failures.</p>

- <p style="text-align: justify"><b>Reduced Latency</b>: Direct event routing and minimized API calls ensure significantly reduced system latencies.</p>

## Impact

<p style="text-align: justify">The adoption and implementation of the event-driven microservice architecture, anchored by AWS EventBridge and SQS, has had profound implications for our e-commerce operations.</p>

1. <p style="text-align: justify"><b>Operational Efficiency</b>: By dramatically reducing redundant API calls and ensuring prompt event processing, the system's operational tempo has noticeably accelerated. This increase in speed translates to quicker reflections of changes across the platform, be it inventory updates, order state changes, or return processing, ensuring that all stakeholders have access to the most recent and relevant data.</p>

2. <p style="text-align: justify"><b>Enhanced Resilience</b>: With the introduction of the Dead Letter Queue (DLQ) and the repushing mechanism, the system can effectively handle events that encounter processing hiccups. This layered approach means that even problematic events are neither lost nor ignored, but instead are isolated, examined, and eventually processed. Such resilience ensures continuity in operations, even in the face of unexpected challenges.</p>

3. <p style="text-align: justify"><b>Scalability and Adaptability</b>: The decoupled nature of the architecture, combined with scalable SQS Consumers, ensures that the system can effortlessly handle event influxes, be it due to seasonal sales, promotional campaigns, or expanded marketplace operations. This adaptability ensures consistent performance, even under varying loads.</p>

4. <p style="text-align: justify"><b>Proactive Monitoring and Management</b>: The integration of AWS CloudWatch means that potential issues are flagged and addressed before they can escalate. This proactive approach minimizes downtimes and ensures consistent high performance, leading to increased trust and reliability among stakeholders.</p>

5. <p style="text-align: justify"><b>Cost Efficiency</b>: By optimizing event routing and processing, and by reducing redundant operations, there's a notable decrease in resource consumption. This efficiency not only ensures better resource utilization but also translates to cost savings in the long run.</p>

6. <p style="text-align: justify"><b>Enhanced User and Seller Experience</b>: As the architecture ensures real-time or near-real-time processing of critical e-commerce events, both end-users (buyers) and sellers benefit from an updated and consistent view of the platform. This synchronization across the platform enhances trust, reduces conflicts or disputes, and fosters a smoother transactional experience.</p>

<p style="text-align: justify">In essence, the architectural enhancements have not only streamlined and strengthened the internal operations but have also played a pivotal role in elevating the overall user experience, leading to higher satisfaction levels and reinforcing the platform's reputation for reliability and efficiency.</p>

## Conclusion
This event-driven microservice design represents a paradigm shift in how events can be optimally routed. Although the core codebase remains proprietary, the architecture, benefits, and results detailed here offer invaluable insights for those looking to optimize their event-driven systems.