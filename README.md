To submit a Spark application as a step using the console


Open the Amazon EMR console at https://console.aws.amazon.com/elasticmapreduce/.

Select the name of your cluster from the Cluster List. The cluster state must be Waiting.

Choose Steps, and then choose Add step.

Configure the step according to the following guidelines:

For Step type, choose Spark application. You should see additional fields for Deploy Mode, Spark-submit options, and Application location appear.

For Name, leave the default value or type a new name. If you have many steps in a cluster, naming each step helps you keep track of them.

For Deploy mode, leave the default value Cluster. For more information about Spark deployment modes, see Cluster mode overview in the Apache Spark documentation.

Leave the Spark-submit options field blank. For more information about spark-submit options, see Launching applications with spark-submit.

For Application location, enter the location of your health_violations.py script in Amazon S3. For example, s3://DOC-EXAMPLE-BUCKET/health_violations.py.

In the Arguments field, enter the following arguments and values:


--data_source s3://DOC-EXAMPLE-BUCKET/food_establishment_data.csv
--output_uri s3://DOC-EXAMPLE-BUCKET/myOutputFolder
							
Replace s3://DOC-EXAMPLE-BUCKET/food_establishment_data.csv with the S3 URI of the input data you prepared in Prepare an application with input data for Amazon EMR.

Replace DOC-EXAMPLE-BUCKET with the name of the bucket you created for this tutorial, and myOutputFolder with a name for your cluster output folder.

For Action on failure, accept the default option Continue so that if the step fails, the cluster continues to run.

Choose Add to submit the step. The step should appear in the console with a status of Pending.

Check for the step status to change from Pending to Running to Completed. To refresh the status in the console, choose the refresh icon to the right of the Filter. The script takes about one minute to run.

You will know that the step finished successfully when the status changes to Completed.



View results




After a step runs successfully, you can view its output results in your Amazon S3 output folder.

To view the results of health_violations.py

Open the Amazon S3 console at https://console.aws.amazon.com/s3/.

Choose the Bucket name and then the output folder that you specified when you submitted the step. For example, DOC-EXAMPLE-BUCKET and then myOutputFolder.

Verify that the following items appear in your output folder:

A small-sized object called _SUCCESS.

A CSV file starting with the prefix part- that contains your results.

Choose the object with your results, then choose Download to save the results to your local file system.

Open the results in your editor of choice. The output file lists the top ten food establishments with the most red violations. The output file also shows the total number of red violations for each establishment.

The following is an example of health_violations.py results.

