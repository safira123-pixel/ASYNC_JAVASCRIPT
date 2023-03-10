# ASYNC JAVASCRIPT PROMISE 

## *Apa pengertian dari Operasi Asynchronous?*

**Operasi asynchronous adalah operasi yang tidak dieksekusi secara langsung pada urutan baris kode yang ditulis, sehingga program tetap dapat berjalan tanpa harus menunggu operasi tersebut selesai. Dalam operasi asynchronous, program dapat melanjutkan eksekusi kode lain selama operasi asynchronous sedang berjalan, sehingga menjaga program tetap responsif dan cepat.**

Contoh dari operasi asynchronous adalah permintaan data melalui jaringan, operasi I/O pada sistem file, dan animasi pada antarmuka pengguna. Dalam semua kasus tersebut, program tidak dapat menentukan dengan pasti kapan operasi tersebut akan selesai, sehingga harus menunggu hingga operasi selesai sebelum melanjutkan eksekusi kode lain.

Untuk menangani operasi asynchronous, JavaScript menggunakan konsep Promise dan callback. Promise adalah sebuah objek yang merepresentasikan nilai atau tugas yang belum selesai, sementara callback adalah sebuah fungsi yang akan dieksekusi setelah operasi asynchronous selesai dilakukan.

Dalam kasus Promise, program dapat menggunakan "then" untuk menentukan tindakan yang harus diambil setelah operasi asynchronous selesai dilakukan (resolve), atau menggunakan "catch" untuk menangani kesalahan (reject) yang terjadi selama operasi asynchronous berlangsung.

Dalam kasus callback, program dapat menentukan sebuah fungsi yang akan dieksekusi setelah operasi asynchronous selesai dilakukan.

Dalam kesimpulannya, operasi asynchronous adalah operasi yang tidak dieksekusi secara langsung pada urutan baris kode yang ditulis, dan dapat ditangani menggunakan konsep Promise dan callback di JavaScript.

## *Apa pengertian dari async javascript promise?*

Async JavaScript Promise adalah konsep di dalam bahasa pemrograman JavaScript yang membantu developer mengelola dan menangani operasi asinkron (asynchronous) yang kompleks.

Promise adalah sebuah objek yang merepresentasikan nilai yang belum tersedia, namun akan tersedia di masa depan ketika operasi asinkron selesai. Dalam praktiknya, Promise digunakan untuk menghindari callback hell dan membuat kode menjadi lebih mudah dipahami dan dikelola.

Async/await adalah fitur baru yang diperkenalkan pada ES8/ES2017 yang memungkinkan penulisan kode asinkron dengan gaya yang mirip dengan kode sinkron. Dengan async/await, pengguna dapat menulis kode asinkron seperti menulis kode sinkron, tanpa harus berurusan dengan callback atau Promise yang kompleks.

Dalam async JavaScript Promise, Anda dapat menggunakan promise untuk melakukan operasi asinkron seperti memuat data dari server atau mengeksekusi fungsi yang membutuhkan waktu yang lama untuk dijalankan, dan kemudian menggunakan async/await untuk menunggu hasil operasi tersebut selesai sebelum melanjutkan eksekusi kode.

## *Pengertian Singkat*

**Promise bisa dikatakan sebagai object yang menyimpan hasil dari sebuah operasi asynchronous baik itu hasil yang diinginkan (resolved value) atau alasan kenapa operasi itu gagal (failure reason).**

Kita ambil contoh seperti saat kita memesan ojek online.

Saat kita mencari driver lewat aplikasi, aplikasi akan berjanji(promise) memberi tahu hasil dari pencarian kita.

Hasilnya bisa diantara dua, yaitu driver ditemukan (resolved value) atau alasan kenapa driver tidak ditemukan(failure reason).

Sebuah Promise berada di salah satu diantara 3 kondisi(state):

1. pending, operasi sedang berlangsung
2. fulfilled, operasi selesai dan berhasil
3. rejected, operasi selesai namun gagal

Sama seperti pada kasus memesan ojek online, status permintaan kita pada aplikasi online diantara tiga kondisi:

1. Mencari driver (pending)
2. Menemukan driver (fulfilled)
3. Driver tidak ditemukan (rejected)

## *Kapan menggunakan async javascript promise*

Async JavaScript Promise digunakan ketika Anda ingin menangani operasi asinkron dalam JavaScript, seperti memuat data dari server, mengambil data dari API, atau mengeksekusi fungsi yang membutuhkan waktu yang lama untuk dijalankan. Berikut ini adalah beberapa contoh penggunaan async JavaScript Promise:

1. Memuat data dari server dengan XMLHttpRequest
```javascript

function loadData(url) {
  return new Promise(function(resolve, reject) {
    var xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.onload = function() {
      if (xhr.status === 200) {
        resolve(xhr.responseText);
      } else {
        reject(xhr.statusText);
      }
    };
    xhr.onerror = function() {
      reject(xhr.statusText);
    };
    xhr.send();
  });
}

loadData('https://example.com/data')
  .then(function(response) {
    console.log(response);
  })
  .catch(function(error) {
    console.error(error);
  });
```

2. Mengambil data dari API dengan fetch()
```javascript

fetch('https://api.example.com/data')
  .then(function(response) {
    if (!response.ok) {
      throw new Error(response.statusText);
    }
    return response.json();
  })
  .then(function(data) {
    console.log(data);
  })
  .catch(function(error) {
    console.error(error);
  });
```

3. Menjalankan operasi I/O yang membutuhkan waktu yang lama
```javascript
function readFile(filePath) {
  return new Promise(function(resolve, reject) {
    var fs = require('fs');
    fs.readFile(filePath, 'utf8', function(error, data) {
      if (error) {
        reject(error);
      } else {
        resolve(data);
      }
    });
  });
}

readFile('/path/to/file')
  .then(function(data) {
    console.log(data);
  })
  .catch(function(error) {
    console.error(error);
  });
```

Dalam ketiga contoh di atas, Promise digunakan untuk menangani operasi asinkron dan menentukan tindakan yang akan diambil ketika operasi selesai, baik berhasil atau gagal. Anda dapat menggunakan then() untuk menentukan tindakan yang akan diambil ketika Promise berhasil di-resolve, atau catch() untuk menentukan tindakan yang akan diambil ketika Promise di-reject.

## *Cara Penggunaan Async JavaScript Promise*

Berikut ini adalah cara penggunaan async JavaScript Promise:

1. Membuat Promise

Untuk membuat Promise, Anda dapat menggunakan constructor Promise yang memiliki satu parameter yaitu fungsi callback yang berisi dua parameter yaitu resolve dan reject. Fungsi resolve digunakan untuk menyelesaikan Promise dengan nilai tertentu, sedangkan fungsi reject digunakan untuk menolak Promise dengan alasan tertentu. 

Berikut contoh penggunaannya:

Template : 

```javascript
const myPromise = new Promise((resolve, reject) => {
  // melakukan operasi asinkron
  // jika operasi berhasil, panggil resolve dengan nilai yang diinginkan
  // jika operasi gagal, panggil reject dengan alasan yang diinginkan
});
```
Contoh : 

```javascript
let progress = 100;
const download = new Promise((resolve, reject) => {
  if (progress === 100) {
    resolve('Download complete');
  } else {
    reject('Download failed');
  }
});
```

2. Menggunakan then() dan catch() untuk menangani Promise

Setelah Promise dibuat, Anda dapat menangani hasilnya dengan then() dan catch(). Metode then() digunakan untuk menentukan tindakan yang akan diambil ketika Promise berhasil di-resolve, sedangkan catch() digunakan untuk menentukan tindakan yang akan diambil ketika Promise di-reject. 

Berikut contoh penggunaannya:

Template : 

```javascript
myPromise
  .then((result) => {
    // tindakan yang akan diambil jika Promise berhasil di-resolve
  })
  .catch((error) => {
    // tindakan yang akan diambil jika Promise di-reject
  });
```
contoh : 

```javascript
  .then((result) => {
    console.log(result); // Download complete
  })
  .catch((error) => {
    console.log(error); // Download failed atau tidak ditampilkan jika tidak ada error
  });
```

3. Menggabungkan Promise dengan Promise.all()

Jika Anda memiliki beberapa Promise yang perlu dijalankan secara paralel, Anda dapat menggunakan Promise.all() untuk menunggu semua Promise selesai dan mengembalikan nilai hasil dari semua Promise. 

Berikut contoh penggunaannya:

Template : 

```javascript
const promises = [
  promise1(),
  promise2(),
  promise3()
];

Promise.all(promises)
  .then((results) => {
    // tindakan yang akan diambil ketika semua Promise berhasil di-resolve
  })
  .catch((error) => {
    // tindakan yang akan diambil jika ada Promise yang di-reject
  });
```
Contoh :
```javascript 
const downloadStart = new Promise((resolve, reject) => {
  resolve('0%');
});
const downloadHalf = new Promise((resolve, reject) => {
  resolve('50%');
});
const downloadFull = new Promise((resolve, reject) => {
  resolve('100%');
});
Promise.all([downloadStart, downloadHalf, downloadFull]).then((result) => {
  console.log(result); // [ '0%', '50%', '100%' ]
});
```

4. Menggunakan async/await

async/await adalah fitur baru dalam JavaScript yang memungkinkan penulisan kode asinkron dengan gaya yang mirip dengan kode sinkron. Dalam async/await, Anda dapat menunggu hasil operasi asinkron sebelum melanjutkan eksekusi kode. 

Berikut contoh penggunaannya:
```javascript
async function myFunction() {
  try {
    const result1 = await promise1();
    const result2 = await promise2();
    const result3 = await promise3();
    // tindakan yang akan diambil jika semua Promise berhasil di-resolve
  } catch (error) {
    // tindakan yang akan diambil jika ada Promise yang di-reject
  }
}
```

## *Kesalahan penggunaan async javascript promise dan contohnya*

Berikut adalah beberapa kesalahan umum dalam penggunaan async JavaScript Promise:

1. Tidak menangani error dengan benar

Jika Promise di-reject, Anda harus menangani error dengan benar menggunakan catch(). Jika Anda tidak menangani error, maka aplikasi akan mengalami kegagalan dan sulit untuk debug. 

Berikut contoh kesalahan penggunaannya:
```javascript
myPromise
  .then((result) => {
    // tindakan yang akan diambil jika Promise berhasil di-resolve
  });
  // tidak menangani error dengan catch()
```
2. Tidak mengembalikan Promise dari fungsi asinkron

Jika Anda membuat fungsi asinkron, pastikan Anda mengembalikan Promise dari fungsi tersebut agar dapat menangani hasilnya dengan then() atau catch(). Jika Anda tidak mengembalikan Promise, maka fungsi tersebut akan mengembalikan nilai undefined dan sulit untuk menangani hasilnya. 

Berikut contoh kesalahan penggunaannya:
```javascript
async function myFunction() {
  // tidak mengembalikan Promise
}

myFunction().then((result) => {
  // tindakan yang akan diambil ketika fungsi berhasil dijalankan
});
```

3. Menggunakan then() secara berantai secara berlebihan

Jika Anda memiliki banyak operasi asinkron yang perlu dijalankan, Anda dapat menggunakan then() secara berantai. Namun, jika Anda menggunakan then() secara berlebihan, kode akan menjadi sulit dibaca dan sulit untuk di-maintain. 

Berikut contoh kesalahan penggunaannya:
```javascript
myPromise
  .then((result1) => {
    // tindakan yang akan diambil jika Promise 1 berhasil di-resolve
    return anotherPromise();
  })
  .then((result2) => {
    // tindakan yang akan diambil jika Promise 2 berhasil di-resolve
    return yetAnotherPromise();
  })
  .then((result3) => {
    // tindakan yang akan diambil jika Promise 3 berhasil di-resolve
  });
```
Sebagai alternatif, Anda dapat menggunakan async/await untuk membuat kode lebih mudah dibaca dan di-maintain.


## *Hal yang mempengaruhi terjadinya kesalahan saat menggunakan async javascript promise*

Beberapa faktor yang mempengaruhi terjadinya kesalahan saat menggunakan async JavaScript Promise adalah:

1. Kurangnya pemahaman tentang konsep Promise

Kurangnya pemahaman tentang konsep Promise dan cara kerjanya dapat menyebabkan kesalahan dalam membuat, menangani, dan menggabungkan Promise. Penting untuk memahami konsep dasar seperti fungsi resolve dan reject, cara mengembalikan nilai dari Promise, serta cara menangani error dengan catch().

2. Kurangnya pengalaman dalam menangani kode asinkron

Kode asinkron dapat lebih sulit untuk dipahami dan di-maintain daripada kode sinkron. Kurangnya pengalaman dalam menangani kode asinkron dapat menyebabkan kesalahan dalam membuat atau menangani Promise.

3. Kurangnya pengalaman dalam debugging kode asinkron

Debugging kode asinkron dapat lebih sulit daripada kode sinkron karena ketidakpastian kapan operasi asinkron akan selesai. Jika ada kesalahan dalam kode asinkron, maka sulit untuk menentukan di mana kesalahan terjadi. Penting untuk menggunakan alat debugging seperti console.log() atau debugger statement untuk membantu menemukan kesalahan.

4. Penggunaan callback yang tidak sinkron dengan benar

Jika Anda menggunakan callback yang tidak sinkron dengan benar, maka dapat menyebabkan kesalahan saat membuat atau menangani Promise. Misalnya, jika Anda menggunakan callback dalam Promise constructor, pastikan callback tersebut bersifat sinkron dan tidak mengandung operasi asinkron.

5. Kesalahan sintaksis dalam kode JavaScript

Kesalahan sintaksis dalam kode JavaScript dapat menyebabkan kesalahan saat menggunakan Promise. Pastikan kode JavaScript Anda bebas dari kesalahan sintaksis dan dapat dijalankan dengan benar.



