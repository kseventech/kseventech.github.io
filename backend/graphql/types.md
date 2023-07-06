The most important difference between `ArgsType` and `InputType` in NestJS with GraphQL lies in their usage and the way
they handle arguments:

- **ArgsType**: Used to define argument types for **individual resolver methods**. It handles individual arguments
  passed as separate parameters.
- **InputType**: Used to define **reusable input types**, typically for mutations or complex input
  structures. `InputType` encapsulates multiple fields within a single input object passed as an argument to the
  resolver method.
