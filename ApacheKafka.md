##### Notes on Apache Kafka study
* Nice Blog to kick start: https://medium.com/better-programming/apache-kafka-in-action-6e19836c9d7b
    * Sequence of steps described:
        * start a zookeeper (with default property)
            * it is mandatory to have zookeeper for kafka because it maintains the namespace and configuration data
               * controller election:
                  * to route to available controller on failure of controllers
               * access control list of all the topics
               * membership of the cluster
               
            * what is the difference between or relation between zookeper and yarn?
               * yarn uses zookeper for resource management
               * yarn manages the cluster nodes to maximize the utilization. However, zookeeper facilitates yarn for the same.
               * zookeeper has its own cluster for its activities, yarn manages entire cluster nodes.
               
        * start a kafka broker ( https://kafka.apache.org/intro )
            * is comparable to that of queing system where the q can be read multiple readers (consumers) with different offset. Each consumers can seek at thier will.
            * retension policy IF set to 2 days then when data is published, post retention period data is delete for freeing up store space.
            * immediate next question is how it is different from db. https://www.percona.com/live/17/sessions/what-apache-kafka-how-it-similar-databases-you-know-and-love-and-how-its-not
               * I may be compared to that of queue files in NSK systems.
                  * No update
                  * sequential read and not random access
                  * no schema , key value pair
                  * records are stored in the form of schema
                  * no sharding: no horizontal partitioning
                        * Shard: some tuples may be present in all the shards (unlike horizontal partitioning)
        * start a topic
            * is like a table but not a table. Related logical records are stored against a topic.
        * start a producer
            * one who feeds the data in the key & value pair to a specific topic
        * start a consumer
            * application subscribes (listens) to a topic. Or it may subscribe to all topic with access.
            * application that processes the data (client application or ml model etc)
        
    * can all consumer read any topic of any producer?
      * yes, by definition but can be controlled through SSL, SASL and ACL 
            * https://medium.com/@stephane.maarek/introduction-to-apache-kafka-security-c8951d410adf
    * A demonstration is provided for a scenario where in which consumer abruptly restarts but successfully is able to read all the messages from beginning.
    
    
