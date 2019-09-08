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
                  * no fixed schema , key value pair
                  * records are stored in the order of arrival
                 
               * No Sharding: only horizontal partitioning - based on the hashing on key.
                  * Shard: some tuples may be present in all the shards (unlike horizontal partitioning)
                  * this helps when there are multiple consumer to a topic to process the data parallel.
                  
               * Replication:
                  * There can be n number brokers in a kafka cluster
                      * n number of cluster node/ brokers are split into One leader and rest followers
                  * producers write into leader and it is leader responsibility to replicate the same to followers
                  * one of follower will become a leader post current leader failure
                    * there may be a data loss when take over happens if the producer has opted to wait till only leader sync and not with replicas
               * Availability
                  * at most : consumer reads a message, update the position and process message. In this case if the failure is post  updation of index, we loose the data when the consumer comes back becuase index is alread forwarded.
                  
                  * at least : consumer reads a message, processes it and then update the position. In this case if the failure happens post processing then the consumer might read the message again and thus leading to duplicate processing.
                  
                  * exactly once: transaction based updation, where in which it rolls back if the consumer fails
                  
        * start a topic
            * is like a table but not a table. Related logical records are stored against a topic.
        * start a producer
            * one who feeds the data in the key & value pair to a specific topic
        * start a consumer
            * application subscribes (listens) to a topic. Or it may subscribe to all topic with access.
            * application that processes the data (client application or ml model etc)
        
    * can all consumer read any topic of any producer?
      * yes, by definition but can be controlled through 
          * SSL(encryption between producer- broker, broker-consumer), 
          * SASL (user and password system) 
          * ACL (access control list) by default zookeeper manage the list and hence it has to secured or encrypted.
          * https://medium.com/@stephane.maarek/introduction-to-apache-kafka-security-c8951d410adf
    * A demonstration is provided for a scenario where in which consumer abruptly restarts but successfully is able to read all the messages from beginning.
    
##### Why streaming is important ?
* Data lake Architecture thrives in the big data era. Data lake includes any/all data in its original form. This enables different users of data lake to transform the data respective to their focus area. Data can be in different format like image, videos, audio etc. and can be streaming data too. Including data lake to include the streaming data makes it more real time data capable. Apache Kafka shines here by connect the streaming source with big data platform. Data from the kafka can piped to any of the Hadoop component there by enabling almost any activity on it as required by the data lake users.
   * nice article on Data lake: https://www.datasciencecentral.com/profiles/blogs/demystifying-data-lake-architecture
    
    
