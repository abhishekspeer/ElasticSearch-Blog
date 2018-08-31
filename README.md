# ElasticSearch-Blog
A basic Blog Application with ElasticSearch functionality implemented.

## Installation
1. Clone or download the repository. 
2. Create a new virtual environment for the project.
    ```bash
    virtualenv venv
    source venv/bin/activate
    ```
3. Install required python libraries giving in the requirements.txt file.
    ```bash
    pip install -r requirements.txt
    ```
4. Run Django migrations.
    
    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```    
5. Perform bulk indexing of data.
    
    * Download elasticsearch and activate it.
    ```bash
    wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.1.1.tar.gz
    tar -xzf elasticsearch-5.1.1.tar.gz
    ./elasticsearch-5.1.1/bin/elasticsearch
    ```
    * Using another terminal, activate the virtualenv and go into the shell for bulk indexing of data.
    ```bash
    python manage.py shell
   
    > from elasticsearchapp.search import *
    > bulk_indexing()
    ```
    * Verify bulk indexing by running this curl command
    ```bash
    curl -XGET 'localhost:9200/blogpost-index/blog_post_index/1?pretty'
    ```
    * Try the search functionality from the shell.
    ```bash
    python manage.py shell
    
    > from elasticsearchapp.search import *
    > print(search(author="<author-name(username) here>"))
    ```
6. Start the application.
    ```bash
    python manage.py runserver
    ```
