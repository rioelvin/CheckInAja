# Main Activity  
Hyperlink lokasi kode program Main Activity.  
[Kode Program MainActivity](../app/src/main/java/hotel/review/appandroid/MainActivity.java)

Kode di atas adalah implementasi dari sebuah MainActivity untuk aplikasi Android bernama "Hotel Review." Aplikasi ini dirancang menggunakan bahasa Java dengan Android SDK. MainActivity mengatur tampilan utama aplikasi, termasuk elemen visual seperti CardView, ImageView, TextView, dan SearchView, serta memberikan animasi untuk meningkatkan pengalaman pengguna.

Penjelasan Tiap Bagian Kode

### 1. Package Declaration
   ```JAVA
   package hotel.review.appandroid;
   ```
   Bagian ini mendeklarasikan nama paket aplikasi Android.

### 2. Import Statements
   Kode ini mengimpor berbagai kelas dari Android SDK untuk menyediakan fungsionalitas:

   - Intent: Untuk berpindah antar aktivitas.
   - Animation: Untuk menerapkan efek animasi.
   - CardView dan SearchView: Untuk tampilan elemen UI. 

### 3. Deklarasi Kelas
   ```JAVA
   public class MainActivity extends AppCompatActivity {
   ```
   Kelas MainActivity adalah kelas utama yang diturunkan dari AppCompatActivity, yang mendukung fitur UI modern.

### 4. Deklarasi Variabel
   ```JAVA
   CardView cardView, cardView2, cardView3;
   ImageView imageView, ImageView2, ImageView3;
   TextView textView, textView2, textView3, textView4, textView5;
   SearchView searchView;
   Animation anim_from_button, anim_from_top, anim_from_left;
   ```
   Variabel ini digunakan untuk merepresentasikan elemen-elemen UI pada layout, seperti:
   
   - CardView: Untuk tampilan kartu interaktif.
   - ImageView: Untuk menampilkan gambar.
   - TextView: Untuk teks deskriptif.
   - SearchView: Untuk pencarian di aplikasi.
   - Animation: Untuk efek transisi pada elemen UI.
   
### 5. Metode onCreate()
  ```JAVA
   @Override
   protected void onCreate(Bundle savedInstanceState) {
  ```
   Metode ini dipanggil saat aktivitas pertama kali dibuat. Berikut adalah penjelasan langkah-langkahnya:

a. Menghubungkan Layout dengan Aktivitas
   ```JAVA
   setContentView(R.layout.activity_main);
   ```
   Kode ini mengatur tampilan aktivitas dengan menggunakan layout activity_main.

b. Menghubungkan Variabel dengan ID di Layout
   ```JAVA
   cardView = findViewById(R.id.cardView);
   imageView = findViewById(R.id.imageView);
   ```
   Kode ini menghubungkan elemen UI di layout XML ke variabel Java menggunakan findViewById().

c. Memuat Animasi
   ```JAVA
   anim_from_button = AnimationUtils.loadAnimation(this, R.anim.anim_from_bottom);
   anim_from_top = AnimationUtils.loadAnimation(this, R.anim.anim_from_top);
   anim_from_left = AnimationUtils.loadAnimation(this, R.anim.anim_from_left);
   Animasi di-load dari file res/anim, yaitu:
   ```
- anim_from_bottom: Animasi dari bawah ke atas.
- anim_from_top: Animasi dari atas ke bawah.
- anim_from_left: Animasi dari kiri ke kanan.
  
d. Menerapkan Animasi
   ```JAVA
   cardView.setAnimation(anim_from_button);
   imageView.setAnimation(anim_from_top);
   searchView.setAnimation(anim_from_left);
   Animasi diterapkan ke elemen-elemen UI.
   ```

e. Listener untuk CardView
   ```JAVA
   cardView.setOnClickListener(new View.OnClickListener() {
   @Override
   public void onClick(View view) {
      Intent secondActivity = new Intent(MainActivity.this, SecondActivity.class);
      startActivity(secondActivity);
      }
   });
   ```
Ketika cardView diklik, aplikasi akan membuka aktivitas baru SecondActivity menggunakan Intent.

f. Menyembunyikan Status dan Navigation Bar
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
Kode ini membuat aplikasi menjadi fullscreen, menyembunyikan status bar dan navigation bar untuk tampilan yang lebih immersive.

----------------------------  

## Struktur Layout yang Diharapkan
Aktivitas ini bergantung pada file layout bernama activity_main.xml, yang memuat elemen-elemen dengan ID sesuai dengan variabel di atas, seperti:
```
cardView, imageView, textView, dan lainnya.
Animasi berada di folder res/anim/.
```
