# Real-Time-Analytics-with-Apache-Spark
Advancing in the field of Big Data and Analytics on the top of it.

* Spark vs tensorflow
https://www.google.com/url?sa=t&source=web&rct=j&url=https://www.analyticsindiamag.com/tensorflow-vs-spark-differ-work-tandem/&ved=2ahUKEwiNhuvepaDiAhVERo8KHSPGAwQQFjACegQIERAP&usg=AOvVaw2fEAxmjv-ua3u70wPqrMpw

* interesting read
https://www.google.com/url?sa=t&source=web&rct=j&url=https://www.quora.com/Why-do-people-integrate-Spark-with-TensorFlow-even-if-there-is-a-distributed-TensorFlow-framework&ved=2ahUKEwiNhuvepaDiAhVERo8KHSPGAwQQFjAFegQIBhAB&usg=AOvVaw2GMqcbLKSCAF4ZUB23LNGt
* https://github.com/maxpumperla/elephas/blob/master/examples/mnist_mlp_spark.py
* https://towardsdatascience.com/pyspark-and-xgboost-integration-tested-on-the-kaggle-titanic-dataset-4e75a568bdb
* https://towardsdatascience.com/deep-learning-with-apache-spark-part-1-6d397c16abd
* https://twitter.com/hashtag/ApacheSpark?src=hash&lang=en

* can we pass the pyspark dataframe to tensorflow?

* Stackoverflow:

  * https://stackoverflow.com/a/56302024/8693106
  * trying to answer https://stackoverflow.com/questions/56297660/which-pyspark-abstraction-is-appropriate-for-my-large-matrix-multiplication
     * Exploring googles colab notebook in cafe.
        * !pip install pyspark
          * installed the pyspark in 10 seconds, there after I m free to start the analysis
          
        * "take" gives the value to the local variable from RDD. Key operation in colab as collect function is not working.
        * co lab gives integration with stackoverflow, with which the exception can be directly queried in stackoverflow.
        * there is a medium post which talks about very large matrix multiplication:
          * https://medium.com/@rantav/large-scale-matrix-multiplication-with-pyspark-or-how-to-match-two-large-datasets-of-company-1be4b1b2871e
           
          * Idea here is to broadcast the matrix B and parallelize matrix A when we need to multiply matrices A & B.
          * Here the matrix multiplication is done vector by vector method.

* Pyspark Cheat Sheet:
  * https://www.qubole.com/resources/pyspark-cheatsheet/
    * df.select("firstName",  Show firstName, df.lastName.like("Smith")).show()
    * https://spark.apache.org/docs/latest/api/python/pyspark.sql.html?highlight=explode for definition of explode.
    * Row (sql function) has .asDict() function converts the row to dictionary for ease of access.
    * Window : readStream, writeStream, output mode (complete, append, update)
    * pyspark.ml.feature ==> StringIndexer : for transforming to string to number 
    * xgboost support through 
    
    ```
    spark.sparkContext.addPyFile("YOUR_PATH/sparkxgb.zip")
    from sparkxgb import XGBoostEstimator
    xgboost = XGBoostEstimator(
        featuresCol="features", 
        labelCol="Survival", 
        predictionCol="prediction"
    )
    ```
    * blazingDB: https://colab.research.google.com/drive/1r7S15Ie33yRw8cmET7_bjCpvjJiDOdub#scrollTo=8AdUt3HiUrc3
      * claims 100x faster than spark
        * uses GPU SQL Engine on RAPIDS
        
    * RDD functions quick recap : https://data-flair.training/blogs/spark-rdd-operations-transformations-actions/

* https://medium.com/@george.seif94/autokeras-the-killer-of-googles-automl-9e84c552a319?source=email-feada7b3aa03-1577569259484-digest.reader------0-59------------------02956d3c_6045_4321_bbeb_9ad30923f27a-1-----&sectionName=top
