# GraphQL Basics

GraphQL is a data query and manipulation language developed by Facebook. It provides an efficient and powerful
alternative to REST.

## Key Concepts:

**1. Single Endpoint**: Unlike REST where you might have multiple endpoints (URLs), in GraphQL you only have a single
endpoint that handles all requests.

**2. Query**: This is a read operation in GraphQL. A client specifies exactly what data it needs in a query, and the
server responds with exactly that data, no more, no less.

**3. Mutation**: This is a write (and update) operation in GraphQL. Like a query, a mutation is also explicit - you
specify the data you want to change and the data you want returned.

**4. Schema & Types**: The schema is a model of the data that can be fetched through the GraphQL server. It defines what
queries and mutations are possible. Every piece of data is associated with a specific type.

**5. Resolver**: These are the functions that the GraphQL server runs to get the data for each query or mutation.

**6. Subscription**: A real-time connection in GraphQL. It allows the server to push updates to the client whenever
specific events occur.

## Advantages of GraphQL:

**1. Efficient Data Loading**: With GraphQL, the client specifies exactly what data it needs, which can reduce the
amount of data that needs to be transferred over the network.

**2. Real-Time Updates**: GraphQL has built-in support for real-time updates with subscriptions.

**3. Strong Typing**: Every piece of data is associated with a specific type, which can make APIs self-documenting and
lead to more robust systems.

**4. Easier to Evolve APIs**: With GraphQL, you can deprecate APIs on a field level, which can make it easier to evolve
your APIs over time.

GraphQL can be a game changer for developing APIs and can provide a highly efficient, powerful and flexible approach.
