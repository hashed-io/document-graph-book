# Features


## End-user Accessibility
The Document Graph Explorer allows for any user with a blockchain account to create and edit content that they own within the graph, and they may create between any two nodes in the graph.

This level of accessibility to non-technical users is unprecedented. It allows them to collaboratively create and connect content with all of the benefits of blockchain. This level of capability was previously only accessible to highly technical engineers.

## File and IPFS Integration
Document Graph has integrated support for storing data or files within IPFS and saving that files’ CID (hash) within the document. 

## Encryption Support
Document Graph Explorer supports encryption of a specific content item’s value. In DGE, the user is prompted to enter a password that is used for symmetric AES encryption. This secret simply encrypts the value and the ciphertext is persisted in the document. 

In a future release, we may integrate with the [Khala/Phala](https://phala.network/en/) confidential blockchain. Also, we are evaluating integration with [PAD](https://www.pad.tech/) as a trustless way to share the secret in a manner that alerts the owner when the secret is accessed. This is useful for interesting use cases such as one-time decrypt use cases and “in case of emergency” use cases.

## GraphQL Caching
Document Graph supports easy integration with [DGraph](https://dgraph.io), an open source distributed graph engine. The document graph cache listens for new blocks, and upon finalization, updates the DGraph graph to reflect any updates to the on-chain graph. DGraph has excellent tooling and ergonomics for querying, custom types or schemas, data visualizer, full-text search, and much more. 

## Composable SDK Experience (CLI)
Document Graph is built to be highly composable and also support an ergonomic developer experience. In addition to the Document Graph Explorer web application, there is a CLI (written in Go) that supports all of the create, read, update, and delete operations directly against the blockchain. 

## Plugin Architecture for Custom Renderers and Editors
Developers can include special fields within their document to enable custom viewers or editors. For example, if the field “preferred_renderer” or “preferred_editor” is populated with an endpoint, this endpoint will be used to render or edit the document.
