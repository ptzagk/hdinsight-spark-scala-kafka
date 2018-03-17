# Use Apache Kafka with Apache Spark on hdinsight


This is a basic example of streaming data to and from Kafka on HDInsight from a Spark on HDInsight cluster. This example uses Kafka DStreams. This example expects Kafka and Spark on HDInsight 3.6.

## How to create Azure subscription using Azure Pass

[Azure Pass homepage](https://www.microsoftazurepass.com/)

[Redemption Process Guide](https://www.microsoftazurepass.com/Home/HowTo)

## How to create Appache Kafka and Spark cluster 

__NOTE__: Apache Kafka and Spark are available as two different cluster types. HDInsight cluster types are tuned for the performance of a specific technology; in this case, Kafka and Spark. To use both together, you must create an Azure Virtual network and then create both a Kafka and Spark cluster on the virtual network. For an example of how to do this using an Azure Resource Manager template, see [https://hditutorialdata.blob.core.windows.net/armtemplates/create-linux-based-kafka-spark-cluster-in-vnet.json](https://hditutorialdata.blob.core.windows.net/armtemplates/create-linux-based-kafka-spark-cluster-in-vnet.json). For an example of using the template with this example, see [Use Apache Spark with Kafka on HDInsight (preview)](https://docs.microsoft.com/azure/hdinsight/hdinsight-apache-spark-with-kafka).

Direct link to cretate full environment
[Deploy to Azure](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fhditutorialdata.blob.core.windows.net%2Farmtemplates%2Fcreate-linux-based-kafka-spark-cluster-in-vnet-v4.1.json)

## Understand this example

This example uses a Scala application in a Jupyter notebook. The code in the notebook relies on the following pieces of data:

* __Kafka brokers__: The broker process runs on each workernode on the Kafka cluster. The list of brokers is required by the producer component, which writes data to Kafka.

* A __Twitter app configuration__: The `Stream-Tweets-To-Kafka.ipynb` notebook uses Twitter to populate data in Kafka. If you do not have a Twitter app set up, visit [](https://apps.twitter.com) to create one.

* __Topic name__: The name of the topic that data is written to and read from. This example expects a topic named `tweets`.

## To run this example

To use the example Jupyter notebooks, you must upload them to the Jupyter Notebook server on the Spark cluster. Use the following steps to upload the notebook:

1. In your web browser, use the following URL to connect to the Jupyter Notebook server on the Spark cluster. Replace __CLUSTERNAME__ with the name of your Spark cluster.

        https://CLUSTERNAME.azurehdinsight.net/jupyter

    When prompted, enter the cluster login (admin) and password used when you created the cluster.

2. From the upper right side of the page, use the __Upload__ button to upload the `Stream-Tweets-To-Kafka.ipynb` file. Select the file in the file browser dialog and select __Open__. 

3. Find the __Stream-Tweets-To-Kafka.ipynb__ entry in the list of notebooks, and select __Upload__ button beside it.

4. Once the file has uploaded, select the __KafkaStreaming.ipynb__ entry to open the notebook. To load tweets into Kafka, follow the instructions in the notebook.

5. Repeat steps 1-3 to upload the `Spark-Streaming-From-Kafka-With-DStreams.ipynb` document to Kafka. Once the file has uploaded, select the entry to open the notebook. Follow the instructions in the notebook to read the tweets from Kafka.