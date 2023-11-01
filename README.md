# envoy-dns-lookups-coredns

we have a potential DNS issue with envoy where it doesn't use the /etc/hosts
correctly and instead asks the DNS server for localhost entries.

## testing

spin up a docker-compose file with the following

* simple API route which is behind envoy
* envoy container with DNS lookups going to coredns
* coredns container with logging enabled to see queries

## outcomes

we really just want to show that envoy is **not** doing silly DNS lookups for
localhost type things.

We use envoy in our k8s cluster where I work and our tooling maps the hostname
of the target container...