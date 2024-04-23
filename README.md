a. program publisher akan mengirim **5 data** ke message broker dalam satu kali jalan. Ini karena ada 5 panggilan ke metode `publish_event` dalam fungsi `main`.

b. URL `amqp://guest:guest@localhost:5672` yang sama di program publisher dan subscriber berarti keduanya berkomunikasi dengan **message broker yang sama**. `localhost:5672` menunjukkan bahwa message broker berjalan di lokal dan mendengarkan port 5672. `guest:guest` adalah kredensial untuk masuk ke message broker.

![alt text](running-rabbitmq.png)
