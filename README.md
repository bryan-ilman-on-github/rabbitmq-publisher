a. program publisher akan mengirim **5 data** ke message broker dalam satu kali jalan. Ini karena ada 5 panggilan ke metode `publish_event` dalam fungsi `main`.

b. URL `amqp://guest:guest@localhost:5672` yang sama di program publisher dan subscriber berarti keduanya berkomunikasi dengan **message broker yang sama**. `localhost:5672` menunjukkan bahwa message broker berjalan di lokal dan mendengarkan port 5672. `guest:guest` adalah kredensial untuk masuk ke message broker.

![alt text](running-rabbitmq.png)

**the publisher sent 5 event to the message broker**

![alt text](publisher-action.png)

**those event later consumed and processed by the subscriber**

![alt text](subscriber-action.png)

There is some spike on the chart because when the publisher program is run, messages enter the server. At that moment, the count of messages rise up from zero briefly and fall down again when the publisher program finish running.

![alt text](publisher-spike.png)
