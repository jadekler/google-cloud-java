Google Cloud Java Client
==========================

Java idiomatic client for [Google Cloud Platform][cloud-platform] services.

[![Build Status](https://travis-ci.org/GoogleCloudPlatform/gcloud-java.svg?branch=master)](https://travis-ci.org/GoogleCloudPlatform/gcloud-java)
[![Coverage Status](https://coveralls.io/repos/GoogleCloudPlatform/gcloud-java/badge.svg?branch=master)](https://coveralls.io/r/GoogleCloudPlatform/gcloud-java?branch=master)

-  [Homepage] (https://googlecloudplatform.github.io/gcloud-java/)
-  [API Documentation] (http://googlecloudplatform.github.io/gcloud-java/apidocs)
-  [Examples] (http://googlecloudplatform.github.io/gcloud-java/apidocs/index.html?com/google/gcloud/examples/package-summary.html)

This client supports the following Google Cloud Platform services:

-  [Google Cloud Datastore] (https://cloud.google.com/datastore/)

<!---
-  [Google Cloud Storage] (https://cloud.google.com/storage/)
--->

> Note: This client is a work-in-progress, and may occasionally
> make backwards-incompatible changes.

Quickstart
----------
Add this to your pom.xml file
```xml
<dependency>
  <groupId>com.google.gcloud</groupId>
  <artifactId>gcloud-java</artifactId>
  <version>LATEST</version>
</dependency>
```

<!---
Example Applications
--------------------

-  `java-datastore-sample`_ - A sample using Cloud Datastore
.. _java-datastore-sample: https://github.com/GoogleCloudPlatform/java-datastore-sample
--->

Google Cloud Datastore
----------------------

Google [Cloud Datastore][cloud-datastore] is a fully managed, schemaless database for
storing non-relational data. Cloud Datastore automatically scales with
your users and supports ACID transactions, high availability of reads and
writes, strong consistency for reads and ancestor queries, and eventual
consistency for all other queries.

See the [Google Cloud Datastore docs][cloud-datastore-activation] for more details on how to activate
Cloud Datastore for your project.

See the ``gcloud-java`` API [datastore documentation][datastore-api] to learn how to interact
with the Cloud Datastore using this Client Library.

```java
import com.google.gcloud.datastore.DatastoreService;
import com.google.gcloud.datastore.DatastoreServiceFactory;
import com.google.gcloud.datastore.DatastoreServiceOptions;
import com.google.gcloud.datastore.Entity;
import com.google.gcloud.datastore.Key;
import com.google.gcloud.datastore.KeyFactory;

DatastoreServiceOptions options = DatastoreServiceOptions.builder().dataset("...").build();
DatastoreService datastore = DatastoreServiceFactory.getDefault(options);
KeyFactory keyFactory = new KeyFactory(datastore).kind("...");
Key key = keyFactory.newKey(keyName);
Entity entity = datastore.get(key);
if (entity == null) {
  entity = Entity.builder(key)
      .set("name", "John Do")
      .set("age", 30)
      .set("updated", false)
      .build();
  datastore.put(entity);
}
```

Contributing
------------

Contributions to this library are always welcome and highly encouraged.

See [CONTRIBUTING] for more information on how to get started.

Java Versions
-------------

Java 7 or above is required for using this client.

Versioning
----------

This library follows [Semantic Versioning] (http://semver.org/).

It is currently in major version zero (``0.y.z``), which means that anything
may change at any time and the public API should not be considered
stable.

License
-------

Apache 2.0 - See [LICENSE] for more information.


[CONTRIBUTING]:https://github.com/GoogleCloudPlatform/gcloud-java/blob/master/CONTRIBUTING.md
[LICENSE]: https://github.com/GoogleCloudPlatform/gcloud-java/blob/master/LICENSE
[cloud-platform]: https://cloud.google.com/
[cloud-datastore]: https://cloud.google.com/datastore/docs
[cloud-datastore-docs]: https://cloud.google.com/datastore/docs
[cloud-datastore-activation]: https://cloud.google.com/datastore/docs/activate
[datastore-api]: http://googlecloudplatform.github.io/gcloud-java/apidocs/index.html?com/google/gcloud/datastore/package-summary.html

[cloud-pubsub]: https://cloud.google.com/pubsub/
[cloud-pubsub-docs]: https://cloud.google.com/pubsub/docs

[cloud-storage]: https://cloud.google.com/storage/
[cloud-storage-docs]: https://cloud.google.com/storage/docs/overview
[cloud-storage-create-bucket]: https://cloud.google.com/storage/docs/cloud-console#_creatingbuckets
