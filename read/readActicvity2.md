# SecondActivity
Hyperlink lokasi kode program Main Activity.  
[Kode Program SecondActivity](../app/src/main/java/hotel/review/appandroid/SecondActivity.java)

Kode ini adalah implementasi dari sebuah aktivitas (Activity) dalam aplikasi Android, yang disebut SecondActivity. Aktivitas ini memiliki fitur untuk menampilkan informasi dengan elemen animasi, transisi antar aktivitas, dan menyembunyikan status bar serta navigasi bar untuk pengalaman layar penuh.

## 1. Pendahuluan
```JAVA
Paket (Package): hotel.review.appandroid
```
Ini menunjukkan bahwa file ini adalah bagian dari paket aplikasi dengan nama tertentu.

Class: SecondActivity  
Class ini adalah turunan dari ```AppCompatActivity```, yang merupakan aktivitas dasar untuk mendukung fitur-fitur modern di aplikasi Android.

## 2. Deklarasi Elemen UI
Beberapa elemen UI yang digunakan dalam layout diinisialisasi, seperti:

- Gambar (ImageView):  
```second_back_arrow``` - Tombol kembali.
```second_arrow_up``` - Ikon panah ke atas untuk transisi.
- Teks (TextView):  
```second_title```, ```second_subtitle```, ```second_rating_number```, ```second_rating_number2```, more_details.
- RatingBar:
```second_ratingbar``` untuk menampilkan rating berbintang.  
Tujuan: Elemen-elemen ini dihubungkan dengan ID dalam layout XML (R.layout.activity_second).

## 3. Fungsi dan Logika
### a. Navigasi ke MainActivity  
```JAVA
second_back_arrow.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        Intent intent = new Intent(SecondActivity.this, MainActivity.class);
        startActivity(intent);
    }
});
```  
Ketika tombol second_back_arrow ditekan, pengguna akan diarahkan kembali ke MainActivity.

### b. Menyembunyikan Status Bar dan Navigasi Bar
```JAVA  
getWindow().setFlags(
    WindowManager.LayoutParams.FLAG_LAYOUT_NO_LIMITS,
    WindowManager.LayoutParams.FLAG_LAYOUT_NO_LIMITS
);
```
```JAVA
this.getWindow().getDecorView().setSystemUiVisibility(
    View.SYSTEM_UI_FLAG_LAYOUT_STABLE
    | View.SYSTEM_UI_FLAG_LAYOUT_HIDE_NAVIGATION
    | View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN
    | View.SYSTEM_UI_FLAG_HIDE_NAVIGATION
    | View.SYSTEM_UI_FLAG_FULLSCREEN
    | View.SYSTEM_UI_FLAG_IMMERSIVE_STICKY
);
```  
Kode ini mengatur agar aplikasi tampil dalam mode layar penuh dengan menyembunyikan:

Status Bar: Area di bagian atas layar yang menampilkan waktu dan ikon sistem.
Navigasi Bar: Tombol virtual seperti "Back" dan "Home" di bagian bawah layar.

### c. Menambahkan Animasi  
```JAVA  
from_left = AnimationUtils.loadAnimation(this, R.anim.anim_from_left);
from_right = AnimationUtils.loadAnimation(this, R.anim.anim_from_right);
from_bottom = AnimationUtils.loadAnimation(this, R.anim.anim_from_bottom);
Animasi diimpor dari file XML di folder res/anim.
Setiap elemen UI memiliki animasi yang diterapkan:
```
```JAVA
second_back_arrow.setAnimation(from_left);
second_title.setAnimation(from_right);
more_details.setAnimation(from_bottom);
```

### d. Navigasi dengan Transisi ke ThirdActivity
```JAVA
second_arrow_up.setOnClickListener(new View.OnClickListener() {
    @RequiresApi(api = Build.VERSION_CODES.LOLLIPOP)
    @Override
    public void onClick(View view) {
        Intent intent = new Intent(SecondActivity.this, ThirdActivity.class);

        Pair[] pairs = new Pair[1];
        pairs[0] = new Pair<View, String>(second_arrow_up, "background_image_transition");

        ActivityOptions options = ActivityOptions.makeSceneTransitionAnimation(SecondActivity.this, pairs);

        startActivity(intent, options.toBundle());
    }
});
```  
Ketika ```second_arrow_up``` ditekan, pengguna akan diarahkan ke ```ThirdActivity```.
Transisi Animasi: Menggunakan API ActivityOptions untuk membuat animasi transisi yang halus (scene transition).  

## 4. Kesimpulan
Kode ini bertujuan untuk menciptakan pengalaman pengguna yang menarik dengan:  
- Navigasi antar layar menggunakan tombol dan transisi animasi.
- Animasi pada elemen-elemen UI untuk meningkatkan estetika.
- Mode layar penuh agar pengguna fokus pada konten aplikasi.
