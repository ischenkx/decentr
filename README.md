# Distributed Cloud Storage
#### Abstract
A semi-decentralized (will be explained later) network that can be used as a cloud storage. There are two types of nodes: heavy (H) and light (L). H's are used for communication and transaction verification (high I/O and CPU usage), L's are "memory cells" (high memory usage).

L's are connected to H's, H's form a distributed network (big-big-big graph). If an L wants to store/load some data, it must proxy requests through H. This allows the H's to leave "footprints" (FP) in the transactions.

The verification of data integrity is based on some POR algorithm and is conducted every N seconds (probably 2-4 hours). Let's call the verification process - VP, data owners - DO, data holders - DH

The most interesting part - economics. Say we have a currency in our system and it can be bought for some existing cryptocurrency (Bitcoin for example). So, each verification process L's DO's pay DH's and H's get some fraction (1-2%) from those transcations.