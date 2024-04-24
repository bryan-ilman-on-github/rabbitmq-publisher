a. program publisher akan mengirim **5 data** ke message broker dalam satu kali jalan. Ini karena ada 5 panggilan ke metode `publish_event` dalam fungsi `main`.

b. URL `amqp://guest:guest@localhost:5672` yang sama di program publisher dan subscriber berarti keduanya berkomunikasi dengan **message broker yang sama**. `localhost:5672` menunjukkan bahwa message broker berjalan di lokal dan mendengarkan port 5672. `guest:guest` adalah kredensial untuk masuk ke message broker.

![alt text](running-rabbitmq.png)

Ketika program publisher dijalankan, maka 5 _event_ akan dikirimkan ke _message broker_ milik RabbitMQ. Selama proses pengiriman _event_ ini berlangsung, jumlah _connection_ pada RabbitMQ dashbard akan bertambah dari nol jadi satu. Pada dashboard, dapat juga dilihat _message rate_ yang dihasilkan program publisher.

![alt text](publisher-action.png)

Begitu ada _event_ yang masuk ke _message broker_, program subscriber akan langsung mengkonsumsinya jika sedang berjalan. Namun, jika program subscriber mati, maka jumlah _message queue_ akan bertambah dan tidak akan berkurang sampai ada yang mengkonsumsinya. Kabar baiknya, _event_ ini tidak akan hilang dan bersifat sangat _durable_ selama _server_ dari RabbitMQ berjalan.

![alt text](subscriber-action.png)

When the publisher program runs, a spike appears on the chart as messages flow into the server. During this time, the message count briefly rises from zero and then falls once the publisher program finishes its operation. This metric indicates the number of messages the publisher generates per second. If the publisher program runs continuously, the spike will flatten out as messages arrive every second. Essentially, the dashboard chart provides insight into the 'message rate'. It reveals the activity level of the publisher program.

![alt text](publisher-spike.png)
