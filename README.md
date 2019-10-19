# spark-stream-processing
A simple stream processing example using Databricks. It shows two examples, one without a trigger, and one with a trigger. 

# Requirements
You'll need a Spark server running. For the example, I used Databricks and built/ran the Jupyter Notebook directly within Databricks. If you're running outside of Databricks, you'll need to use a client programming model, which is quite different than what's here.

You'll also need the baby names data - here's where I got it: https://github.com/bellevue-university/dsc650/tree/master/data

# Running This
You'll need to run each step of the Jupyter Notebook in order. You'll eventually stream - `gender_count_query = gender_count.writeStream.queryName('gender_counts').format('memory').outputMode('complete').start()` without the trigger **OR** `gender_count_query = gender_count.writeStream.queryName('gender_counts').format("memory").trigger(processingTime='30 seconds').outputMode('complete').start()` with the trigger (you should only run one at a time - be sure to stop one before starting the other). That gets everything ready.

Next, you'll run one of the two `for` loops. (Each correspond to a stream.) When you do that, you'll need to upload `.csv` files into Databricks - about one every 10 seconds. I only did this with 10 files, but you can do it however you want to noting that the `for` loop will run for the amount of time specified no matter how often (or how many) `.csv` files you upload.

# Comments
This code is very easily modifiable for any type of stream processing. 
