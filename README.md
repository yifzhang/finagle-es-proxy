finagle-es-proxy
================

This is an example of using [finagle] (https://github.com/twitter/finagle) as a proxy to [Elasticsearch] (http://elasticsearch.org).
It demonstrates proxying using the Elasticsearch native client, and creating an authentication layer in front of Elasticsearch.

The ESProxy object is a server (created using the cool [Twitter Server] (https://github.com/twitter/twitter-server) template) that proxies all requests to an Elasticsearch cluster.
The cluster settings (hosts and cluster name) can be controlled via initialization parameters (see the [ESProxy] (https://github.com/rore/finagle-es-proxy/blob/master/src/main/scala/io/github/rore/ESProxy.scala) code).

Doing a simple HTTP proxy to Elasticsearch is rather trivial. But building a proxy using the Elasticsearch native client requires a little hacking. We need to pass the request to the REST controller of Elasticsearch, provide it with a mock channel to capture the response and return it in our own server.

This example also shows how to add an authentication filter to the server which can be used to secure Elasticsearch for unauthorized access.



