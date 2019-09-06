##### Notes on Apache Kafka study
* Nice Blog to kick start: https://medium.com/better-programming/apache-kafka-in-action-6e19836c9d7b
    * Sequence of steps described:
        * start a zookeeper (with default property)
        * start a kafka broker ( https://kafka.apache.org/intro )
            * is comparable to that of queing system where the q can be read multiple readers (consumers) with different offset. Each consumers can seek at thier will.
            * retension policy IF set to 2 days then when data is published, post retention period data is delete for freeing up store space.
        * start a topic
        * start a produce
        * start a consumer
        
    * A demonstration is provided for a scenario where in which consumer abruptly restarts but successfully is able to read all the messages from beginning.
    
    
