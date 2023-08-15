# Belajar Typescript

TypeScript memiliki Implicit, Explicit, dan Ambient types, saya coba pakai Ambient types,
Ambient types adalah tipe yang ditambahkan ke cakupan eksekusi global.

Langkah Pertama :

* npm init -y
* npm install typescript --save-dev
* npx tsc --init


```
npm install @types/node --save-dev
```

tsconfig.json (versi umum)

```
{
  "compilerOptions": {
    "target": "ES6",
    "outDir": "./dist",
    "rootDir": "./src"
  }
}

```

---

Buat folder baru bernama "src", lalu buat file bernama index.ts

dan di dalam nya isi dengan :

```
console.log('hello world')
```

Lalu Compile.

**Compile:**
npx tsc 

Ketika compile selesai akan ada folder baru bernama "build".

Code yang di compile akan berada di dalam **build/index.js**  .

---

```
npm install --save-dev ts-node nodemon
```

## Cold Reloading

agar bisa running tanpa menunggu compiled dan juga nodemon, cocok untuk local development

Lalu bikin file nodemon.json untuk config nya :

```
{
  "watch": ["src"],
  "ext": ".ts,.js",
  "ignore": [],
  "exec": "npx ts-node ./src/index.ts"
}
```

Lalu tambahkan 

```
"start:dev": "npx nodemon",
```

tinggal running pakai :
npx nodemon

---

## Creating production builds

Untuk membuat code clean dan compile project untuk production, kita tambahkan build script.

Instal "rimraf", sebuah cross-platform tool berfungsi seperti rm-rf (hanya menghapus apa yang anda ingin hapus).

Lalu tambahkan ini di package.json

```
"build": "rimraf ./build && tsc",
```

Sekarang kita bisa jalankan **npm run build**, nah rimraf akan menghapus buiild folder kita yang lama yang sebeleum compiler ke code baru di dalam **dist**.

---

### Production startup script

Untuk menjalakan app di dalam tahap production, kita butuh command run build dulu yang nanti di ekseskusi compile javascript nya ke build/index.js

**Command :**
```
"start": "npm run build && node build/index.js"
```

---

### Scripts overview

npm run start:dev
Starts aplikasi di mode development menggunakan nodemon dan ts-node untuk cold reloading.

npm run build
Builds the app at build, cleaning the folder first.

npm run start
Starts the app in production by first building the project with npm run build, and then executing the compiled JavaScript at build/index.js.

---

Done, terima kasih.
