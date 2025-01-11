# ThirdActivity.java

Kode ini adalah implementasi aktivitas (Activity) dalam aplikasi Android yang bernama ThirdActivity. Aktivitas ini memiliki fitur tampilan layar penuh, animasi pada elemen UI, navigasi antar aktivitas, dan membuka tautan Google Maps.

### 1. Pendahuluan
Paket (Package): ```hotel.review.appandroid```  
File ini merupakan bagian dari aplikasi untuk review hotel.  

Class: ThirdActivity  
Class ini adalah turunan dari ```AppCompatActivity```, yang digunakan untuk aktivitas dengan fitur modern di Android.  

### 2. Deklarasi Elemen UI
Beberapa elemen UI yang digunakan adalah:

- ImageView:  
   ```down_arrow``` Ikon panah ke bawah untuk navigasi ke aktivitas sebelumnya.  
- ScrollView:  
   ```third_scrollview``` Area scroll untuk menampilkan konten panjang.  
- Button:  
   ```roadmapButton``` Tombol untuk membuka Google Maps.  
- Inisialisasi:
  Elemen-elemen ini dihubungkan dengan ID dalam layout XML ```R.layout.activity_third```.  

### 3. Fungsi dan Logika  
a. Animasi Elemen UI  
```JAVA
from_bottom = AnimationUtils.loadAnimation(this, R.anim.anim_from_bottom);
down_arrow.setAnimation(from_bottom);
third_scrollview.setAnimation(from_bottom);
```  
Animasi diambil dari file XML res/anim/anim_from_bottom.xml.
Elemen ```down_arrow``` dan ```third_scrollview``` diberi efek animasi muncul dari bawah layar.  

------------------------------  

b. Navigasi Antar Aktivitas  
Navigasi ke SecondActivity:  
```JAVA  
down_arrow.setOnClickListener(new View.OnClickListener() {
    @RequiresApi(api = Build.VERSION_CODES.LOLLIPOP)
    @Override
    public void onClick(View view) {
        Intent intent = new Intent(ThirdActivity.this, SecondActivity.class);

        Pair[] pairs = new Pair[1];
        pairs[0] = new Pair<View, String>(down_arrow, "background_image_transition");

        ActivityOptions options = ActivityOptions.makeSceneTransitionAnimation(ThirdActivity.this, pairs);
        startActivity(intent, options.toBundle());
    }
});
```

Ketika ```down_arrow``` ditekan, pengguna diarahkan kembali ke SecondActivity.
- Transisi Animasi: Menggunakan ActivityOptions untuk memberikan efek transisi yang halus antara dua aktivitas.  
------------------------------  

c. Membuka Google Maps
```JAVA
roadmapButton.setOnClickListener(view -> {
    String mapUrl = "https://maps.app.goo.gl/dP5tBgAann1yMEC68";

    Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(mapUrl));
    intent.setPackage("com.google.android.apps.maps"); // Membuka dengan Google Maps
    startActivity(intent);
});
```  
- Fungsi Tombol: Ketika tombol roadmapButton ditekan, aplikasi membuka tautan Google Maps menuju lokasi tertentu.
Intent:
- ```ACTION_VIEW``` digunakan untuk membuka tautan.
- ```Uri.parse(mapUrl)``` memproses tautan lokasi.
- ```setPackage("com.google.android.apps.maps")``` memastikan Google Maps yang digunakan, jika tersedia.
------------------------------  

d. Menyembunyikan Status Bar dan Navigasi Bar
```JAVA
getWindow().setFlags(
    WindowManager.LayoutParams.FLAG_LAYOUT_NO_LIMITS,
    WindowManager.LayoutParams.FLAG_LAYOUT_NO_LIMITS
);

this.getWindow().getDecorView().setSystemUiVisibility(
    View.SYSTEM_UI_FLAG_LAYOUT_STABLE
    | View.SYSTEM_UI_FLAG_LAYOUT_HIDE_NAVIGATION
    | View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN
    | View.SYSTEM_UI_FLAG_HIDE_NAVIGATION
    | View.SYSTEM_UI_FLAG_FULLSCREEN
    | View.SYSTEM_UI_FLAG_IMMERSIVE_STICKY
);
```
Kode ini menyembunyikan:

- Status Bar: Area atas layar yang menampilkan informasi sistem.
- Navigasi Bar: Tombol virtual seperti "Back" dan "Home".
- Tujuan: Memberikan pengalaman layar penuh yang lebih imersif.
------------------------------  

## 4. Kesimpulan
Kode ThirdActivity.java memiliki fitur utama berikut:

- Animasi: Menambahkan efek animasi pada elemen UI agar lebih menarik.
- Navigasi Antar Aktivitas: Menggunakan animasi transisi untuk berpindah ke aktivitas lain.
- Integrasi Google Maps: Membuka lokasi langsung di Google Maps melalui tombol dengan intent khusus.
- Mode Layar Penuh: Menyembunyikan status bar dan navigasi bar untuk memberikan pengalaman pengguna yang fokus pada konten.
