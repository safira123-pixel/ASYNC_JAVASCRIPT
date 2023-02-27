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

```javascript
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

## *Callback Hell vs Promise dan contohnya*

Callback hell dan Asynchronous Promise adalah dua konsep yang terkait dengan cara JavaScript menangani kode asynchronous, namun memiliki perbedaan signifikan dalam cara penulisannya.

Callback hell terjadi ketika program memiliki banyak operasi asynchronous yang harus dijalankan secara berurutan, dan setiap operasi memerlukan callback untuk mengeksekusi kode setelah operasi tersebut selesai. Contoh dari callback hell adalah seperti berikut:

```javascript
getData(function (data1) {
  getMoreData(data1, function (data2) {
    getMoreData(data2, function (data3) {
      getMoreData(data3, function (data4) {
        // dan seterusnya ...
      });
    });
  });
});
```

Dalam kode di atas, setiap operasi asynchronous memerlukan callback untuk mengeksekusi kode setelah operasi selesai dilakukan. Hal ini menyebabkan kode menjadi sulit dibaca dan dipahami, serta sulit untuk dikelola.

Sedangkan dalam Asynchronous Promise, program menggunakan Promise untuk menangani operasi asynchronous, sehingga kode menjadi lebih mudah dipahami dan dikelola. Contoh dari Asynchronous Promise adalah seperti berikut:

```javascript
getData()
  .then(function (data1) {
    return getMoreData(data1);
  })
  .then(function (data2) {
    return getMoreData(data2);
  })
  .then(function (data3) {
    return getMoreData(data3);
  })
  .then(function (data4) {
    // dan seterusnya ...
  })
  .catch(function (error) {
    console.error(error);
  });
```
Dalam kode di atas, setiap operasi asynchronous dikemas dalam sebuah Promise, sehingga program dapat menggunakan "then" untuk menentukan tindakan yang harus diambil setelah operasi selesai dilakukan, atau menggunakan "catch" untuk menangani kesalahan yang terjadi selama operasi asynchronous berlangsung. Kode ini lebih mudah dipahami dan dikelola daripada callback hell.

Dalam kesimpulannya, callback hell terjadi ketika program memiliki banyak operasi asynchronous yang harus dijalankan secara berurutan, sementara Asynchronous Promise menggunakan Promise untuk menangani operasi asynchronous, sehingga kode menjadi lebih mudah dipahami dan dikelola.