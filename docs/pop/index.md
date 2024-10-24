# NDP Point-of-Presence

The NDP Point-of-Presence (POP) enables distributed access to data and services across a federated network. Each POP serves as a local access point, providing users with customizable services and workflows tailored to specific data needs.

## Key Components

The NDP POP is built around several core components: 

### Federation Orchestration

- Manages and coordinates multiple NDP POPs within the federated network.
- Ensures synchronization of services and data across different POP locations.
- Provides a unified interface for overseeing the operation and integration of POPs into the broader NDP ecosystem.

### Service Stacks

POPs support a range of service stacks that can be customized based on user needs:

#### Standard NDP Services:

- Catalog: Centralized indexing and retrieval of data.
- Search: Advanced search capabilities across the data catalog.
- Data Democratization: Provides access to data in user-friendly formats.

#### sciDX Stack:
- Data Staging Service: Prepares data for analysis or processing.
- Data Streaming Service: Facilitates real-time data streaming for dynamic analysis.
- In-situ Processing: Supports data processing directly at the point of collection or storage.
- Third-Party Stacks: Integrate external services for specialized needs.

### NDP POP Factory

A deployment mechanism that sets up and updates service stacks across different POPs. This mechanism facilitates the creation of new POP instances and the customization of existing ones. Furthermore, the POP Factory ensures consistent deployment of services in line with the federation’s standards.

### Workflow Composition

Users can develop and execute workflows by interfacing with the POPs through:

- APIs: Programmatic access to data and services.
- Python Client Library: Enables Python-based interaction with the NDP services.

These tools support the integration of data retrieval, processing, and analysis into user-defined workflows.

### Deployment Models

NDP POPs can be deployed in various environments to suit different infrastructure needs:

- [Docker](https://www.docker.com/): Standalone deployment for local testing or development.
- [Kubernetes](https://kubernetes.io/): Cluster-based deployment for scalability and load balancing.
- Cloud: Integration with cloud platforms for enhanced accessibility and resource management.
- HPC (High-Performance Computing): Supports intensive computation and data processing needs.