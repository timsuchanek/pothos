![Pothos](./website/public/assets/logo-name-auto.svg)

## Pothos - A plugin based GraphQL schema builder for typescript

Pothos makes writing graphql schemas in typescript easy, fast and enjoyable. The core of Pothos adds
0 overhead at runtime, and has `graphql` as its only dependency.

By leaning heavily on typescripts ability to infer types, Pothos is the most type-safe way of
writing GraphQL schemas in typescript/node while requiring very few manual type definitions and no
code generation.

Pothos has a unique and powerful plugin system that makes every plugin feel like its features are
built into the core library. Plugins can extend almost any part of the API by adding new options or
methods that can take full advantage of the Pothos type system.

## Hello, World

```typescript
import { ApolloServer } from 'apollo-server';
import SchemaBuilder from '@pothos/core';

const builder = new SchemaBuilder({});

builder.queryType({
  fields: (t) => ({
    hello: t.string({
      args: {
        name: t.arg.string(),
      },
      resolve: (parent, { name }) => `hello, ${name || 'World'}`,
    }),
  }),
});

new ApolloServer({
  schema: builder.toSchema({}),
}).listen(3000);
```

## Full docs available at https://pothos-graphql.dev

## Plugins that make Pothos even better

- ## [Scope Auth](https://pothos-graphql.dev/plugins/scope-auth)
  Add global, type level, or field level authorization checks to your schema
- ## [Validation](https://pothos-graphql.dev/plugins/validation)
  Validating your inputs and arguments
- ## [Dataloader](https://pothos-graphql.dev/plugins/dataloader)
  Quickly define data-loaders for your types and fields to avoid n+1 queries.
- ## [Relay](https://pothos-graphql.dev/plugins/relay)
  Easy to use builder methods for defining relay style nodes and connections, and helpful utilities
  for cursor based pagination.
- ## [Simple Objects](https://pothos-graphql.dev/plugins/simple-objects)
  Define simple object types without resolvers or manual type definitions.
- ## [Mocks](https://pothos-graphql.dev/plugins/mocks)
  Add mock resolver for easier testing
- ## [Sub-Graph](https://pothos-graphql.dev/plugins/sub-graph)
  Build multiple subsets of your graph to easily share code between internal and external APIs.
- ## [Directives](https://pothos-graphql.dev/plugins/directives)
  Integrate with existing schema graphql directives in a type-safe way.
- ## [Smart Subscriptions](https://pothos-graphql.dev/plugins/smart-subscriptions)
  Make any part of your graph subscribable to get live updates as your data changes.
- ## [Errors](https://pothos-graphql.dev/plugins/errors)
  A plugin for easily including error types in your GraphQL schema and hooking up error types to
  resolvers.
- ## [**Prisma**](https://pothos-graphql.dev/plugins/prisma)
  A plugin for more efficient integration with prisma that can help solve n+1 issues and more
  efficiently resolve queries
- ## [**Complexity**](https://pothos-graphql.dev/plugins/complexity)
  A plugin for defining and limiting complexity of queries

## Dev setup

See [CONTRIBUTING.md](./CONTRIBUTING.md)
