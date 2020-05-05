
<h1> Membuat Apache Spark Cluster Menggunakan Docker </h1>
<h2> Membuat Apache Spark Cluster </h2>
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
4. Kita dapat melakukan tes spark cluster dengan melakukan web UI <br> 
<img src="dokumentasi1/22100_5.jpg"><br>

<h2> Menjalankan Script Python di Dalam Apache Spark Cluster </h2>
1. Ketik docker ps untuk melihat container yang sedang berjalan<br>
2. Masuklah ke dalam container dan mengeksekusi bash dengan menggunakan perintah berikut: docker exec -it <container_id> /bin/bash. Container id diisi dengan id dari spark master<br>
3. Cek alamat IP dengan menggunakan perintah berikut : hostname -i <br>
<img src="dokumentasi1/22100_3.jpg"><br>
4. Untuk melakukan submit job, Apache Spark menyediakan command spark-submit. <br>
Lakukan perintah berikut : spark-submit --master spark://172.18.0.4:7077 examples/src/main/python/pi.py 10 <br>
5. Tunggu sampe proses selesai <br>
<img src="dokumentasi1/22100_4.jpg"><br>

<h2> Tugas membandingkan </h2>
Lakukan percobaan dengan mengganti parameter-parameter berikut:<br>
Jumlah worker: 2, 5<br>
Jumlah CPU: 2, 4<br>
Memory: 1G<br>
Partisi: 100, 1000<br>

1. Lakukan cara2 diatas dari awal membuat spark cluster sampai dengan menjalankan pi.py di dalam CMD. <br>
2. Kita bandingkan 2 worker dengan 2 CPU antara 100 dan 1000 partisi <br>
<img src="dokumentasi1/perb1.jpg"><br><br>
3. Kita bandingkan 2 worker dengan 4 CPU antara 100 dan 1000 partisi <br>
<img src="dokumentasi1/2w4c.jpg"><br><br>
4. Kita bandingkan 5 worker dengan 2 CPU antara 100 dan 1000 partisi <br>
<img src="dokumentasi1/5w2c.jpg"><br><br>
5. Kita bandingkan 5 worker dengan 4 CPU antara 100 dan 1000 partisi <br>
<img src="dokumentasi1/5w4c.jpg"><br><br>
Note : waktu proses selesai dari 1000 partisi selalu berada di bag atas (yang memiliki waktu lebih lama) sedangkan 100 partisi yg bagian bawah <br>

<h2> Kesimpulan </h2>
