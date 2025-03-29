```mermaid
C4Context
    title Context Diagram - Billing System

    Person(customer, "Customer", "User who makes payments.")
    Person(external-system, "Payment Provider", "Payment system (e.g., Stripe, PayPal)")

    System(billing-system, "Billing System", "Manages payments and subscriptions.")
    System_Ext(redis, "Redis", "Queue management system used by Bull.")

    Rel(customer, billing-system, "Makes payment requests (Product subscription)", "HTTP")
    Rel(external-system, billing-system, "Sends webhooks with payment events", "Webhook")
    Rel(billing-system, redis, "Publishes payment events to the queue (Bull + Redis)", "Queue")

    Layout_Neighboring(customer, external-system)
    Layout_Neighboring(billing-system, redis)

```
