# GraphQL Subscriptions

GraphQL's subscriptions are a real-time feature in GraphQL that allows a server to send data updates to the clients that
chose to listen to them. They're particularly useful in applications where you want live updates, such as chats, live
feeds, notifications, etc.

## Key Concepts:

**1. Persistent Connection**: Unlike typical request-response flow in HTTP, GraphQL subscriptions maintain a long-lived
connection between client and server. This connection is usually a WebSocket, but can be any transport that allows
pushing data to the client.

**2. Event-driven**: Subscriptions are event-based. When a particular event that a client is subscribed to occurs, the
server sends a message with the data related to that event to the client.

**3. Selective Listening**: Just like with queries and mutations, clients can specify exactly what data they want to
listen for in their subscription.

**4. Multiple Subscriptions**: A client can have multiple active subscriptions with the server, each listening for
different events.

**5. Server Push**: Data is pushed from server to client, not pulled as with queries or mutations.

Using GraphQL subscriptions can add a level of complexity to your application, but they are an incredibly powerful tool
for building real-time functionality.
