##My System designing notes

Things to look for while designing a system

Shared nothing architecture
With this architecture, each node is able to operate independently of one another and there is no central "brain" managing state or coordinating activities for the other nodes.

Redundancy
Maintain redundancy of service & data

Availability
Reliability
Performance
Scalability
Managability
Cost

Decouple services : Eg. upload & download. Can scale them independently. Uploads can exaust connections, hence better decouple from download

Use CDNs for caching/delivery

Pole Position, an open source tool for DB benchmarking, http://polepos.org/ 

Flickr solves this read/write issue by distributing users across different shards such that each shard can only handle a set number of users (Create pools)

Creating redundancy in a system can remove single points of failure and provide a backup or spare functionality if needed in a crisis.

When it comes to horizontal scaling, one of the more common techniques is to break up your services into partitions, or shards. 

The design would require a naming scheme that tied an image's filename to the server containing it. An image's name could be formed from a consistent hashing scheme mapped across the servers. Or alternatively, each image could be assigned an incremental ID, so that when a client makes a request for an image, the image retrieval service only needs to maintain the range of IDs that are mapped to each of the servers (like an index).

Local Caching vs Global Caching

	Option 1 : Global cache where cache is responsible for retrieval
	
	Option 2 : Global cache where request nodes are responsible for retrieval
	
Proxy Servers - Collapsed Forwarding

	A way to use a proxy to speed up data access is to collapse the same (or similar) requests together into one request, and then return the single result to the requesting clients.
	
	Imagine there is a request for the same data (let's call it littleB) across several nodes, and that piece of data is not in the cache. If that request is routed thought the proxy, then all of those requests can be collapsed into one, which means we only have to read littleB off disk once.
	
	Use  Squid (http://www.squid-cache.org/) and Varnish (https://www.varnish-cache.org/intro/index.html#intro)
	
DB Indexing

Loadbalancers

Think about queues

