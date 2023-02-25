# ASYNC JAVASCRIPT AWAITS 

## *Pengertian dari async awaits*

Async/await adalah fitur dalam pemrograman asinkron pada bahasa pemrograman modern seperti JavaScript yang memungkinkan pengembang untuk menulis kode asinkron dengan lebih mudah dan intuitif.

Dalam program asinkron, sebuah operasi atau tugas mungkin memerlukan waktu yang lama untuk dieksekusi dan menyelesaikan, seperti mengambil data dari database atau memanggil API. Selama menunggu operasi selesai, program dapat melakukan tugas lain yang tidak memerlukan waktu yang lama.

Async/await memungkinkan pengembang untuk menulis kode yang tidak memblokir atau menghentikan eksekusi program, dan akan berlanjut ketika operasi asinkron selesai. Async/await memungkinkan pengembang untuk menulis kode asinkron seperti kode synchronous, membuatnya lebih mudah untuk membaca, memahami, dan memelihara kode.

Ketika kode diawali dengan kata kunci "async", itu menunjukkan bahwa kode tersebut adalah fungsi asinkron, dan dalam fungsi asinkron, operator "await" digunakan untuk menunda eksekusi kode sampai operasi asinkron selesai. Setelah operasi selesai, nilai yang dihasilkan oleh operasi asinkron dapat diakses dan digunakan oleh kode berikutnya.

## *Kapan menggunakan async awaits?*

Async/await biasanya digunakan dalam kasus-kasus di mana program perlu melakukan operasi yang memerlukan waktu yang lama, seperti mengambil data dari server atau melakukan operasi I/O. Beberapa kasus penggunaan async/await antara lain:

1. Mengambil data dari server

Saat mengambil data dari server, Anda harus menunggu hingga server merespons permintaan Anda sebelum melanjutkan eksekusi program. Async/await memungkinkan Anda untuk menangani operasi ini secara asinkron tanpa menghentikan eksekusi program.

2. Operasi I/O

Ketika melakukan operasi I/O seperti membaca atau menulis file, waktu yang dibutuhkan untuk menyelesaikan operasi tersebut mungkin cukup lama. Async/await memungkinkan program untuk melanjutkan eksekusi saat operasi I/O sedang berlangsung, sehingga program tidak terblokir dan masih dapat melakukan tugas-tugas lain.

3. Tugas-tugas berulang

Jika Anda perlu menjalankan beberapa tugas berulang atau tugas yang saling bergantung, async/await memungkinkan Anda untuk mengeksekusinya secara asinkron, sehingga program dapat melanjutkan tugas lainnya selama tugas asinkron sedang berjalan.

4. Komunikasi dengan API

Saat berinteraksi dengan API, program harus menunggu hingga permintaan ke API selesai dan respon diterima. Async/await memungkinkan program untuk menangani operasi ini secara asinkron, sehingga program dapat melanjutkan eksekusi dan melakukan tugas-tugas lain selama menunggu respon dari API.

Dalam ringkasan, async/await digunakan ketika Anda ingin melakukan operasi yang membutuhkan waktu yang lama atau operasi yang memerlukan akses ke sumber daya eksternal, dan Anda ingin menghindari pemblokiran eksekusi program ketika menunggu operasi selesai.

## *Kapan menggunakan async awaits*

Async/await cocok digunakan ketika program harus melakukan operasi yang membutuhkan waktu yang lama atau operasi yang memerlukan akses ke sumber daya eksternal seperti server atau database. Ini mencegah program terjebak atau terblokir saat menunggu operasi selesai. Beberapa contoh penggunaan async/await adalah:

1. Mengambil data dari server

Ketika program perlu mengambil data dari server, penggunaan async/await memungkinkan program untuk menunggu hingga data diterima tanpa memblokir atau menghentikan eksekusi program.

````javascript

async function getDataFromServer() {
  const response = await fetch('https://example.com/data');
  const data = await response.json();
  console.log(data);
}
````

2. Operasi I/O

Ketika program melakukan operasi I/O seperti membaca atau menulis file, penggunaan async/await memungkinkan program untuk melanjutkan eksekusi saat operasi I/O sedang berlangsung, sehingga program tidak terblokir.
````javascript
async function readFile() {
  const fileHandle = await fs.promises.open('/path/to/file', 'r');
  const contents = await fileHandle.readFile();
  console.log(contents);
  await fileHandle.close();
}
````

3. Tugas-tugas berulang
Jika program perlu menjalankan beberapa tugas berulang atau tugas yang saling bergantung, penggunaan async/await memungkinkan program untuk mengeksekusinya secara asinkron, sehingga program dapat melanjutkan tugas lainnya selama tugas asinkron sedang berjalan.
````javascript
async function doTasks() {
  const task1 = await doTask1();
  const task2 = await doTask2(task1);
  const task3 = await doTask3(task2);
  console.log(task3);
}
````

4. Komunikasi dengan API

Ketika program berinteraksi dengan API, penggunaan async/await memungkinkan program untuk menangani operasi ini secara asinkron, sehingga program dapat melanjutkan eksekusi dan melakukan tugas-tugas lain selama menunggu respon dari API.

````javascript
async function fetchDataFromAPI() {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  console.log(data);
}
````

Dalam semua contoh di atas, penggunaan async/await memungkinkan program untuk menangani operasi asinkron secara mudah dan intuitif, dan mencegah program terjebak atau terblokir saat menunggu operasi selesai.

## *Cara menggunakan async awaits*

Async/await adalah fitur JavaScript yang memungkinkan Anda menangani operasi asinkron dengan cara yang lebih mudah dan intuitif. Berikut adalah langkah-langkah untuk menggunakan async/await:

Deklarasikan fungsi sebagai async dengan menambahkan kata kunci "async" sebelum kata kunci "function".

````javascript
async function myAsyncFunction() {
  // ...
}
````

Di dalam fungsi async, gunakan kata kunci "await" sebelum operasi asinkron yang ingin Anda tangani.

````javascript
async function myAsyncFunction() {
  const result = await doSomethingAsynchronous();
  // ...
}
````

Fungsi async mengembalikan nilai Promise, sehingga Anda dapat menggunakan metode .then() atau await lagi di luar fungsi async untuk menangani hasilnya.

````javascript
async function myAsyncFunction() {
  const result = await doSomethingAsynchronous();
  return result;
}
myAsyncFunction()
  .then(result => console.log(result))
  .catch(error => console.error(error));
````

Jika ada beberapa operasi asinkron yang perlu dijalankan secara bersamaan, Anda dapat menggunakan Promise.all() untuk menunggu semua operasi selesai.

````javascript
async function myAsyncFunction() {
  const [result1, result2, result3] = await Promise.all([
    doSomethingAsynchronous1(),
    doSomethingAsynchronous2(),
    doSomethingAsynchronous3(),
  ]);
  // ...
}
````

Jika ada beberapa operasi asinkron yang saling bergantung, Anda dapat menggunakan await untuk menunggu hasil operasi sebelumnya selesai.

````javascript
async function myAsyncFunction() {
  const result1 = await doSomethingAsynchronous1();
  const result2 = await doSomethingAsynchronous2(result1);
  const result3 = await doSomethingAsynchronous3(result2);
  // ...
}
````

Dalam kesimpulan, async/await adalah fitur yang sangat berguna dalam JavaScript untuk menangani operasi asinkron. Dengan mengikuti langkah-langkah di atas, Anda dapat menggunakan async/await dengan mudah dan menghindari callback hell atau kode yang sulit dibaca dan dipahami.

## *Kesalahan penggunaan async awaits dan contohnya*

Beberapa kesalahan umum dalam penggunaan async/await adalah:

1. Tidak menangani error dengan benar

Karena async/await adalah fitur yang sangat baru, beberapa pengembang mungkin tidak menyadari bahwa Anda masih perlu menangani error seperti yang dilakukan dengan Promise. Ini dapat mengakibatkan kesalahan yang sulit dilacak dan mempengaruhi kinerja aplikasi.

````javascript
// contoh kesalahan
async function myAsyncFunction() {
  const response = await fetch('https://example.com/data');
  const data = await response.json();
  console.log(data);
}
````

Jika request ke server gagal, kode di atas tidak akan menangani error. Seharusnya ditangani dengan try/catch:

````javascript
async function myAsyncFunction() {
  try {
    const response = await fetch('https://example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
````

2. Tidak mengeksekusi fungsi async dengan benar

Fungsi async harus dipanggil dengan menambahkan tanda kurung setelah nama fungsi. Jika tidak, itu hanya akan mengembalikan Promise dan tidak akan mengeksekusi kode di dalam fungsi.

````javascript
// contoh kesalahan
async function myAsyncFunction() {
  // ...
}

myAsyncFunction; // tidak dieksekusi

// harusnya
myAsyncFunction(); // dieksekusi
````

3. Tidak menunggu Promise selesai

Salah satu manfaat dari async/await adalah dapat menunggu Promise selesai dengan menggunakan kata kunci await. Namun, jika tidak menunggu Promise selesai, itu bisa menyebabkan kode yang tidak konsisten dan tidak diharapkan.

````javascript
// contoh kesalahan
async function myAsyncFunction() {
  const result = doSomethingAsynchronous();
  console.log(result);
}

// harusnya
async function myAsyncFunction() {
  const result = await doSomethingAsynchronous();
  console.log(result);
}
````

Dalam kesimpulan, async/await adalah fitur yang sangat berguna dalam JavaScript, tetapi bisa menjadi sulit dipahami jika tidak digunakan dengan benar. Untuk menghindari kesalahan, pastikan Anda menangani error, mengeksekusi fungsi async dengan benar, dan menunggu Promise selesai dengan kata kunci await.

## *Hal yang mempengaruhi terjadinya kesalahan saat menggunakan async awaits*

Beberapa hal yang mempengaruhi terjadinya kesalahan saat menggunakan async/await adalah sebagai berikut:

1. Kesalahan logika program

Kesalahan logika program dapat terjadi jika pengembang tidak memahami konsep dasar async/await atau tidak memperhatikan bagaimana data diproses di dalam fungsi asinkron. 

Contoh kesalahan logika program adalah melakukan operasi synchronously di dalam fungsi async, atau melakukan operasi secara parallel tanpa memperhatikan dependensi antar operasi.

2. Tidak menangani error

Jika operasi asinkron yang dilakukan mengalami kesalahan atau terjadi kesalahan di dalam fungsi asinkron, dan error tidak ditangani dengan benar, hal ini dapat menyebabkan program gagal dan menyebabkan bug yang sulit dilacak.

3. Callback hell

Kode yang menggunakan callback hell atau penggunaan callback yang terlalu dalam akan menyebabkan kode sulit dibaca dan dipahami. Penggunaan async/await untuk mengatasi callback hell sangat disarankan untuk meningkatkan keterbacaan dan memudahkan dalam penanganan error.

4. Ketidaksinkronan data

Jika data yang diproses secara asinkron tidak disinkronkan dengan benar, ini dapat menyebabkan kesalahan dalam program. Hal ini dapat terjadi jika data tidak dikembalikan dengan benar atau ketika ada operasi asinkron yang tidak dijalankan dengan benar.

5. Kesalahan dalam pemanggilan fungsi

Kesalahan ini dapat terjadi ketika fungsi async tidak dipanggil dengan benar atau jika ada kesalahan dalam menunggu hasil dari fungsi async. Hal ini dapat terjadi jika pengembang tidak memahami konsep dasar async/await atau tidak memperhatikan bagaimana data diproses di dalam fungsi asinkron.

Untuk menghindari kesalahan saat menggunakan async/await, penting untuk memahami konsep dasar async/await dan memperhatikan bagaimana data diproses di dalam fungsi asinkron. Selain itu, pastikan untuk menangani error dengan benar, menghindari callback hell, dan sinkronkan data dengan benar.

