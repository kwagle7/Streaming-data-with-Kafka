# Streaming-data-with-Kafka
Download and install Kafka and start streaming data using Kafka

Objectives:
- Download and install Kafka
- Start the Zookeeper server for Kafka metadata management
- Start the Kafka message broker service
- Create a topic
- Start a producer
- Start a consumer

 # Download and Extract Kafka
  <pre>
   wget https://archive.apache.org/dist/kafka/2.8.0/kafka_2.12-2.8.0.tgz 
  </pre>
# Extract Kafka
<pre>
  tar -xzf kafka_2.12-2.8.0.tgz
</pre>

# Start Zookeper
<img width="600" alt="image" src="https://github.com/kwagle7/Streaming-data-with-Kafka/assets/13037108/5da90402-7275-4314-b86e-e74fea9c89ea">

Zookeeper is required for Kafka to work. Start the Zookeeper server.
ZooKeeper is responsible for the overall management of Kafka cluster.
It monitors the Kafka brokers and notifies Kafka if any broker or partition goes down, or if a new broker or partition goes up.
<pre>
cd kafka_2.12-2.8.0
bin/zookeeper-server-start.sh config/zookeeper.properties
</pre>
![image](https://github.com/kwagle7/Streaming-data-with-Kafka/assets/13037108/a6dbeaa8-c5f2-4caf-bf2f-7c049585c8cd)

![image](https://github.com/kwagle7/Streaming-data-with-Kafka/assets/13037108/d0ef1359-8161-47df-90c5-efc65844168a)
You can sure it has started when you see an output like this:



# Start the kafka broker service
Start a new terminal.
Run the commands below. This will start the Kafka message broker service.
<pre>
cd kafka_2.12-2.8.0
bin/kafka-server-start.sh config/server.properties
</pre>
![image](https://github.com/kwagle7/Streaming-data-with-Kafka/assets/13037108/bc1d3f77-0db9-4675-ad77-a2c61fdbad34)

![image](https://github.com/kwagle7/Streaming-data-with-Kafka/assets/13037108/2e908529-70bc-427d-8fe6-f22f7f225951)

# Create a topic
You need to create a topic before you can start to post messages.
to create a topic named news, start a new terminal and run the command below.
<pre>
cd kafka_2.12-2.8.0
bin/kafka-topics.sh --create --topic news --bootstrap-server localhost:9092
</pre>

# Start Producer
You need a producer to send messages to Kafka. Run the command below to start a producer.
<pre>
  bin/kafka-console-producer.sh --topic news --bootstrap-server localhost:9092
</pre>
Once the producer starts, and you get the ‘>’ prompt, type any text message and press enter. Or you can copy the text below and paste. The below text sends three messages to kafka.
<pre>
Good morning
Good day
Enjoy the Kafka lab
</pre>
# Start Consumer
You need a consumer to read messages from kafka.

Open a new terminal.

Run the command below to listen to the messages in the topic news.
<pre>
  cd kafka_2.12-2.8.0
  bin/kafka-console-consumer.sh --topic news --from-beginning --bootstrap-server localhost:9092
</pre>
You should see all the messages you sent from the producer appear here.

You can go back to the producer terminal and type some more messages, one message per line, and you will see them appear here.

# Explore Kafka directories.

Kafka uses the directory /tmp/kakfa-logs to store the messages.

Explore the folder news-0 inside /tmp/kakfa-logs.

This is where all the messages are stored.

Explore the folder /home/project/kafka_2.12-2.8.0

# Clean Up
Delete the Kafka installation file.
<pre>
  rm kafka_2.12-2.8.0.tgz
</pre>
