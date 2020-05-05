
<h1> Membuat Apache Spark Cluster Menggunakan Docker </h1>
1. Buat file docker-compose.yml yang berisi : <br>

  version: '2'<br>

  services:<br>
    spark:<br>
      image: bitnami/spark:2<br>
      environment:<br>
        - SPARK_MODE=master<br>
        - SPARK_RPC_AUTHENTICATION_ENABLED=no<br>
        - SPARK_RPC_ENCRYPTION_ENABLED=no<br>
        - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no<br>
        - SPARK_SSL_ENABLED=no<br>
      ports:<br>
        - '8080:8080'<br>
    spark-worker-1:<br>
      image: bitnami/spark:2<br>
      environment:<br>
        - SPARK_MODE=worker<br>
        - SPARK_MASTER_URL=spark://spark:7077<br>
        - SPARK_WORKER_MEMORY=1G<br>
        - SPARK_WORKER_CORES=1<br>
        - SPARK_RPC_AUTHENTICATION_ENABLED=no<br>
        - SPARK_RPC_ENCRYPTION_ENABLED=no<br>
        - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no<br>
        - SPARK_SSL_ENABLED=no<br>
        - SPARK_MASTER_URL=spark://spark:7077<br>
    spark-worker-2:<br>
      image: bitnami/spark:2<br>
      environment:<br>
        - SPARK_MODE=worker<br>
        - SPARK_WORKER_MEMORY=1G<br>
        - SPARK_WORKER_CORES=1<br>
        - SPARK_RPC_AUTHENTICATION_ENABLED=no<br>
        - SPARK_RPC_ENCRYPTION_ENABLED=no<br>
        - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no<br>
        - SPARK_SSL_ENABLED=no<br>
    spark-worker-3:<br>
      image: bitnami/spark:2<br>
      environment:<br>
        - SPARK_MODE=worker<br>
        - SPARK_MASTER_URL=spark://spark:7077<br>
        - SPARK_WORKER_MEMORY=1G<br>
        - SPARK_WORKER_CORES=1<br>
        - SPARK_RPC_AUTHENTICATION_ENABLED=no<br>
        - SPARK_RPC_ENCRYPTION_ENABLED=no<br>
        - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no<br>
        - SPARK_SSL_ENABLED=no<br>
    spark-worker-4:<br>
      image: bitnami/spark:2<br>
      environment:<br>
        - SPARK_MODE=worker<br>
        - SPARK_MASTER_URL=spark://spark:7077<br>
        - SPARK_WORKER_MEMORY=1G<br>
        - SPARK_WORKER_CORES=1<br>
        - SPARK_RPC_AUTHENTICATION_ENABLED=no<br>
        - SPARK_RPC_ENCRYPTION_ENABLED=no<br>
        - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no<br>
        - SPARK_SSL_ENABLED=no<br>
    spark-worker-5:<br>
      image: bitnami/spark:2<br>
      environment:<br>
        - SPARK_MODE=worker<br>
        - SPARK_MASTER_URL=spark://spark:7077<br>
        - SPARK_WORKER_MEMORY=1G<br>
        - SPARK_WORKER_CORES=0<br>
        - SPARK_RPC_AUTHENTICATION_ENABLED=no<br>
        - SPARK_RPC_ENCRYPTION_ENABLED=no<br>
        - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no<br>
        - SPARK_SSL_ENABLED=no<br>
        <br>
2. Jalankan perintah docker-compose up<br>
<img src="dokumentasi1/22100_1.jpg"><br>
3. Cek kontainer dengan docker-ps<br>
<img src="dokumentasi1/22100_3.jpg"><br>

