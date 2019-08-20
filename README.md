# Google Summer of Code 2019
This page summarizes the work done as part of Google Summer of Code 2019 project; it contains links to github pull requests, performance analysis document, presentation slides, and code documentation.

### Project Description: [Spark and Parquet Backend for cBioPortal Web API](https://summerofcode.withgoogle.com/projects/#5105508921376768) 
cBioPortal utilizes a Spring MVC architecture with MyBatis for the persistence layer and a relational database (MySQL) for data storage. As the number and size of cancer datasets increase, high-performance computing and storage will only become more vital in providing an adequate cBioPortal user experience. The primary goals of this project are to use Spark and Parquet to improve the performance of the existing web APIs and to provide a high-performance computing platform for future development.

### Pull Requests
All 7 APIs used in Study View page were implemented, reviewed and merged for the proof of concept.

1. [Parquet writer utility & mutated-genes api](https://github.com/cBioPortal/cbioportal/pull/6334) - 
Java program for writing data files into Parquet formated files and backend code and junit tests for mutated-genes/fetch api.

2. [Clinical-data apis](https://github.com/cBioPortal/cbioportal/pull/6386) -
Backend code and junit tests for clinical-data-count, clinical-data-bin-counts, clinical-data-density-plot apis.

3. [Filtered-samples api](https://github.com/cBioPortal/cbioportal/pull/6440) - Backend code and junit tests for filtered-samples api.

4. [Sample-counts api](https://github.com/cBioPortal/cbioportal/pull/6475) - Backend code and junit tests for sample-counts api.

5. [Cna-genes api](https://github.com/cBioPortal/cbioportal/pull/6483) - Backend code and junit tests for cna-genes and copy-number-enrichments apis.

6. [Documentation](https://github.com/cBioPortal/cbioportal/pull/6494) - Documentation for new Spark configuration properties and Organization of Parquet files and naming conventions.

### Performance Analysis documentation
Performance analysis was done locally with small (1k), medium (10k), and large (60k, 240k samples) datasets. The results show that Spark implementation doesn't improve performance on small datasets, but it improves performance with some APIs and large datasets.  
* [Performance analysis document (PDF)](./spark-parquet-performance.pdf)

### Presentation Slides presented to cBioPortal community (8/12/2019)
All 6 GSoC students working with cBioPortal presented our projects in cBioPortal community meetings.
My presentation slides include the background of the project, Spark application components, Parquet writing utilities, performance analysis, and Spark UI for monitoring the application.
* [Presentation slides (PDF)](./spark-parquet-slides.pdf)

### Documentation
* [Spark & Parquet properties](https://github.com/cBioPortal/cbioportal/blob/spark-parquet-persistence/docs/portal.properties-Reference.md#spark--parquet)
* [Study View Customization with Spark & Parquet](https://github.com/cBioPortal/cbioportal/blob/spark-parquet-persistence/docs/Spark-Parquet-Data-Loading.md)

### Lessons Learned
Incorporating a new technology stack to an existing application always comes with a number of challenges - from a hybrid mode or fully migrated approach to selecting the right technologies for the application. Presenting the project to the cBioPortal community resulted in good discussion and suggestions: possibly using a Cassandra databse that is scalable with low latency and testing Spark's parallelization in AWS. To migrate to Spark and Parquet technology stack, there are still some analysis and experiments that we should do in the environment that is comparable to cBioPortal production environment; however this proof of concept provides insights into what benefits we may get from using Spark and Parquet. 
