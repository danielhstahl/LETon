## LETon

This library focuses on the "E" of the [LET](https://medium.com/@danstahl1138/let-the-next-evolution-of-etl-and-elt-f82c0683bcc) approach to data movement.  

### Design principles

Human readable YAML to define entities which are represented by data.  This should be created in a "whiteboarding" session with the appropriate stakeholders.

### Architecture

Assumed that there exists a CDC abstraction that pushes deltas to Kafka topic(s).  This library extracts elements from these topics and then publishes to a distinct Kafka topic.  

### Open questions

* Should this library help define the "low-latency"/application layer for joining source systems?  Or should we assume that source systems are already appropriately modeled?

* If we don't believe that source systems are appropriately modeled should we assume the output of this library is sent to a low latency layer first?  If so, then we can output deeply nested objects.  If not, we would likely want more structured/relational output.

* Should this be implementation agnostic?  (spark vs kinesis/lambda, for example)

* Will this library facilitate creation of this "output" topic?  

* How to handle complex transformations?  Completely arbitrary/custom?  Or prebuilt?  See the [example](./schema_example/consumer.yaml) for areas which may need complex logic.

## Alternative approaches considered and discarded

UI for defining data objects.  Additional complexity and not as "free form" as YAML.  YAML is declarative and can be versioned with the rest of your code.
