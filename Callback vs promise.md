# ASYNC JAVASCRIPT PROMISE 
## *Callback vs Promise dan contohnya*

Callback dan Promise adalah dua pendekatan yang digunakan dalam JavaScript untuk menangani kode asinkron. 

Berikut perbandingan antara Callback dan Promise:

Callback :

1. Menggunakan fungsi callback untuk menangani kode asinkron
2. Callback biasanya memiliki dua parameter, yaitu error dan data
3. Callback bersifat asinkron dan dijalankan saat operasi asinkron selesai
4. Callback dapat di-nesting atau di-chain secara berlebihan, yang dapat mengakibatkan callback hell
5. Callback tidak dapat menangani beberapa operasi asinkron secara bersamaan

Promise :

1. Menggunakan objek Promise untuk menangani kode asinkron
2. Promise memiliki tiga status, yaitu pending, fulfilled, dan rejected
3. Promise bersifat asinkron dan dijalankan saat operasi asinkron selesai
4. Promise dapat di-chaining menggunakan then() dan catch(), yang membuat kode lebih mudah dibaca dan di-maintain
5. Promise dapat menangani beberapa operasi asinkron secara bersamaan menggunakan Promise.all() atau Promise.race()

Keuntungan menggunakan Promise adalah kode lebih mudah dibaca dan di-maintain, lebih mudah untuk menangani error, dan dapat menangani beberapa operasi asinkron secara bersamaan. 

Sedangkan kekurangannya adalah lebih kompleks daripada callback dan memerlukan waktu dan usaha untuk mempelajarinya.

Keuntungan menggunakan Callback adalah mudah dipelajari dan digunakan, dan cocok untuk skenario sederhana. 

Namun, kelemahannya adalah kode sulit dibaca dan di-maintain jika terlalu banyak nested callback, sulit untuk menangani error, dan tidak dapat menangani beberapa operasi asinkron secara bersamaan.

Seiring dengan kemajuan teknologi, penggunaan Promise lebih direkomendasikan daripada Callback. Namun, terkadang Callback masih digunakan dalam beberapa kasus tertentu, seperti pada kode legacy atau integrasi dengan library lama yang masih menggunakan Callback.

Berikut adalah perbandingan antara Callback dan Promise beserta contoh penggunaannya:

Callback:

```scss
// Contoh penggunaan callback
function getUser(userId, callback) {
  setTimeout(() => {
    if (userId === 1) {
      callback(null, { id: 1, name: "John" });
    } else {
      callback("User not found", null);
    }
  }, 1000);
}

// Memanggil fungsi getUser dengan callback
getUser(1, (err, user) => {
  if (err) {
    console.log(err);
  } else {
    console.log(user);
  }
});
```

Pada contoh di atas, kita menggunakan callback untuk menangani kode asinkron pada fungsi getUser yang akan mengambil data user berdasarkan ID-nya dari database. Fungsi getUser akan mengeksekusi callback setelah operasi asinkron selesai, dengan mengembalikan error atau data user.

Promise:

```javascript
// Contoh penggunaan Promise
function getUser(userId) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (userId === 1) {
        resolve({ id: 1, name: "John" });
      } else {
        reject("User not found");
      }
    }, 1000);
  });
}

// Memanggil fungsi getUser dengan Promise
getUser(1)
  .then((user) => {
    console.log(user);
  })
  .catch((err) => {
    console.log(err);
  });
```

Pada contoh di atas, kita menggunakan Promise untuk menangani kode asinkron pada fungsi getUser yang akan mengambil data user berdasarkan ID-nya dari database. Fungsi getUser akan mengembalikan objek Promise yang memiliki tiga status, yaitu pending, fulfilled, dan rejected. Kita dapat menangani status Promise menggunakan metode then() dan catch(), yang akan dieksekusi saat Promise fulfilled atau rejected.

Dalam kedua contoh di atas, keduanya digunakan untuk menangani kode asinkron dalam mengambil data user dari database. Namun, dengan menggunakan Promise, kode menjadi lebih mudah dibaca dan di-maintain daripada menggunakan callback.
