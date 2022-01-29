# Distributed Cloud Storage
## Abstract
A semi-decentralized (will be explained later) network that can be used as a cloud storage. There are two types of nodes: heavy (H) and light (L). H's are used for communication and transaction verification (high I/O and CPU usage), L's are "memory cells" (high memory usage).

L's are connected to H's, H's form a distributed network (big-big-big graph). If an L wants to store/load some data, it must proxy requests through H. This allows the H's to leave "footprints" (FP) in the transactions.

The verification of data integrity is based on some POR algorithm and is conducted every N seconds (probably 2-4 hours). Let's call the verification process - VP, data owners - DO, data holders - DH

The most interesting part - economics. Say we have a currency in our system and it can be bought for some existing cryptocurrency (Bitcoin for example). So, each verification process L's DO's pay DH's and H's get some fraction (1-2%) from those transcations.

## Implementation ideas
### Users
1. Each user is represented in a system by their ID.

### Data representation
1. All files are of the same size - 256MB (I call it a 'batch' later on). Seems like it's possible to use an arbitary size for a batch, but in my opinion, it's much better to keep it constant to reduce the total amount of transactions. For example 1 petabyte of information is about 4e6 transactions.
2. Each file has some metadata, that is used for the verification algorithm. It must be of constant size.

### Storing
DO - data owner, F - file
1. DO (L) sends a request to its parent node (H). H looks for a potential DH in its subtree. If the lookup fails, then H sends requests to the neighbours and waits for the response.
2. When the DH is found, it's given the address of the DO. Then we build a direct tunnel between these nodes and transfer the batch.
3. Now, we have to register the batch for the verification process in future (both DH and DO are interested in this). For this purpose, DO generates metadata and sends a register request to H. Now H can insert its name inside this transaction and get taxes in future.
