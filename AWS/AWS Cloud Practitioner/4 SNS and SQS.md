## SNS (Simple Notification Service)
**Overview:** #SNS is a fully managed publish/subscribe messaging service that allows you to send messages to multiple subscribers through a single message.
- **Topics and Subscriptions:**
    - **Topics:** Create a topic to which messages can be published. Each topic has a unique Amazon Resource Name (ARN).
    - **Subscriptions:** Entities can subscribe to topics to receive notifications. Supported protocols include:
        - HTTP/HTTPS (webhooks)
        - Email/Email-JSON
        - Short Message Service (SMS)
        - Lambda functions
        - Application endpoints (for mobile devices)
- **Use Cases:**
    - Sending alerts and notifications (e.g., system alerts, application updates).
    - Fan-out messaging where a single message is sent to multiple subscribers.
    - Event-driven architectures where applications respond to changes in data or state.
## SQS (Simple Queue Service)
 #SQS is a fully managed message queuing service that enables decoupled communication between distributed application components.
- **Message Processing:**
    - Messages sent to SQS remain in the queue until they are processed and deleted by consumers.
    - **Visibility Timeout:** After a message is received by a consumer, it becomes invisible to other consumers for a specified time, allowing the first consumer to process it without interference.
- **Types of Queues:**
    - **Standard Queue:** Offers at-least-once delivery and allows for unlimited throughput, but messages may be delivered out of order.
    - **FIFO Queue (First-In-First-Out):** Ensures that messages are processed exactly once and in the order they are sent.
- **Use Cases:**
    - Decoupling microservices, where one service can send messages to a queue and another can process them asynchronously.
    - Buffering requests to handle spikes in load.