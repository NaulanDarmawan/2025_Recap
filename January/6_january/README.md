Hari ini Aku belajar tentang Jetpack Compose, suatu tata cara pembuatan aplikasi terbaru dari
tim Google mulai pada tahun 2020. Konsep ini memudahkan Aku banget dalam memahami 
bagaimana cara kita membuat aplikasi android dengan cara berfokus pada kode kotlin saja, 
tanpa harus layouting melalui file xml yang dimana menurutku ini cukup mempermudah banget jauh
karena kalau masih pakai xml, agak sulit saat kita mau menampilkan banyak data, apalagi dari
API aplikasi lain, perlu adapter & banyak kode boilerplate yang perlu kita tuliskan.
Berbeda dengan Jetpack Compose yang dimana kita hanya perlu berfokus di satu file kotlin
dan Boom, kita bisa bikin layout dengan sangat cepat. Di haru pertama coba coba research
teknologi Jetpack Compose ini aku dapat kesimpulan bahwa tata cara Jetpack Compose
mirip dengan bagaimana kita melalukan programming di Framework Flutter.
<hr>
# Ini contoh perbandingan kotlin sebelum & sesudah memakai Jetpack Compose dalam bikin UI

Sebelum menggunakan Jetpack Compose, layout UI aplikasi Android biasanya dibuat menggunakan XML. Berikut adalah contoh sederhana layout XML untuk menampilkan teks dan tombol.

### Kode XML (Sebelum Compose)

```xml
<!-- res/layout/activity_main.xml -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/helloText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello, World!"
        android:textSize="24sp" />

    <Button
        android:id="@+id/myButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click Me" />
</LinearLayout>

// MainActivity.kt
package com.example.myapp

import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val helloText = findViewById<TextView>(R.id.helloText)
        val myButton = findViewById<Button>(R.id.myButton)

        myButton.setOnClickListener {
            helloText.text = "Button Clicked!"
        }
    }
}
```

### Kode (Setelah Compose)

```xml
// MainActivity.kt
package com.example.myapp

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.Column
import androidx.compose.material.Button
import androidx.compose.material.Text
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface
import com.example.myapp.ui.theme.MyAppTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            MyAppTheme {
                // A surface container using the 'background' color from the theme
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = MaterialTheme.colorScheme.background
                ) {
                    Greeting()
                }
            }
        }
    }
}

@Composable
fun Greeting() {
    var textState by remember { mutableStateOf("Hello, World!") }

    Column(
        modifier = Modifier.padding(16.dp)
    ) {
        Text(text = textState, style = MaterialTheme.typography.headlineMedium)
        Button(onClick = {
            textState = "Button Clicked!"
        }) {
            Text("Click Me")
        }
    }
}
```

Kelihatan bedanya bukan, sebelumnya kita perlu dua file yaitu xml dan file kotlin untuk membuat
satu tampilan, setelah adanya Jetpack Compose kita cukup butuh File Kotlin saja
yang tentunya mempermudah kita kedepannya. Mantap sih untuk diresearch lebih lanjut, nais 😎😎
---- Have A Good Day All 💖💖 ----