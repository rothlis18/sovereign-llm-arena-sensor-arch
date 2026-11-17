To design a system architecture for a real-time distributed sensor network that integrates various data sources, ensures fault tolerance, and meets strict latency requirements, the architecture must be built on a foundation of distributed computing principles, leveraging microservices and edge computing. The architecture will consist of the following components:

1. **Data Ingestion Layer**: Utilize a distributed message broker (e.g., Apache Kafka) to handle high-throughput data ingestion from heterogeneous sensors. This layer ensures low-latency data streaming and supports backpressure management.

2. **Edge Processing Nodes**: Deploy edge computing nodes close to sensor locations to perform initial data processing, filtering, and aggregation. This reduces latency by minimizing data transmission to central servers and offloads processing from the core network.

3. **Centralized Data Processing and Storage**: Implement a scalable data processing framework (e.g., Apache Flink or Apache Spark) for real-time analytics and data storage. Use distributed databases (e.g., Cassandra or CockroachDB) to ensure high availability and fault tolerance.

4. **Fault Tolerance Mechanisms**: Employ redundancy and replication strategies across all layers. Use consensus algorithms (e.g., Raft or Paxos) for distributed state management and ensure failover capabilities with load balancers and container orchestration platforms (e.g., Kubernetes).

5. **Security Measures**: Integrate end-to-end encryption for data in transit and at rest. Implement role-based access control (RBAC) and continuous monitoring for anomaly detection using machine learning models.

6. **Scalability and Modularity**: Design the system using microservices architecture to ensure modularity. Each service should be independently deployable and scalable, allowing for horizontal scaling as demand increases.

7. **Non-Functional Requirements Linkage**: Map non-functional requirements to functional ones using a traceability matrix. For example, link scalability to the ability to handle increased sensor data volume, and security to data encryption protocols.

8. **Testable Metrics**: Define key performance indicators (KPIs) such as latency (measured in milliseconds), throughput (measured in messages per second), and uptime (measured in percentage). Use automated testing frameworks to validate these metrics continuously.

9. **Verification Strategies**: Implement continuous integration/continuous deployment (CI/CD) pipelines with automated testing for both functional and non-functional requirements. Use chaos engineering to test system resilience and fault tolerance under various failure scenarios.

10. **Operational Compliance**: Conduct regular audits and performance reviews to ensure compliance with specifications. Use monitoring tools (e.g., Prometheus, Grafana) to track system performance and health in real-time.

By structuring the architecture with these components and strategies, the system will achieve the necessary balance of modularity, performance, and maintainability while ensuring compliance with both functional and non-functional specifications across all operational scenarios.