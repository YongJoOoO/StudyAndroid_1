## π¦ 43κ°. μλ² νλ‘κ·Έλλ° μ€λΉ

### βΆοΈ μλ² νλ‘κ·Έλλ° κ°μ

- μλλ‘μ΄λ μ νλ¦¬μΌμ΄μκ³Ό ν΅μ ν  μλ² νλ‘κ·Έλ¨ κ΅¬ν μν μ€λΉ μμ μν
- μλ²λ jsp, spring, nodejs, python λ± μΉ μλΉμ€λ₯Ό μν΄ **λ°± μλ κ°λ°μ ν  μ μλ κ² μ€ νΈν κ² μ¬μ©**
- μ¬κΈ°μλ jspλ₯Ό νμ©νλ€.

### **π§ μ€μΉ μννΈμ¨μ΄**

- Java Development Kit : 8λ²μ 
- Eclipse
- Apache-Tomcat : 9λ²μ 
- MySQL : λ°μ΄ν°λ² μ΄μ€

## π¦ 44κ°. λ°μ΄ν°λ² μ΄μ€ μμ±

### βΆοΈ λ°μ΄ν°λ² μ΄μ€ νμ΄λΈ κ΅¬μ‘°

**1) user_table : μ¬μ©μ νμ μ λ³΄ νμ΄λΈ**

![νμ.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/70e83b3d-c258-4d8b-bf8e-deeaf179c8f6/%ED%9A%8C%EC%9B%90.png)

**2) board_table : κ²μν μ λ³΄**

![κ°μνμ λ³΄.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2afa45ea-98c2-462a-84b9-83532bfffd53/%EA%B0%9C%EC%8B%9C%ED%8C%90%EC%A0%95%EB%B3%B4.png)

**3) content_table : κ²μκΈ λ΄μ© μ λ³΄** 

![sλ΄μ©.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/adc0f7b0-68f8-4ebf-b824-2de4565faea8/s%EB%82%B4%EC%9A%A9.png)

### **π§ μ μ²΄ νμ΄λΈ κ΅¬μ‘° κ΄κ³λ**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/657094b1-fe4c-4a67-8b8e-1860b4c2ac3e/Untitled.png)

### **π§ MySQL μ Sql μΏΌλ¦¬λ¬Έ μμ±**

```sql
create database app3_community_db;

use app3_community_db;

create table user_table(
user_idx int not null primary key auto_increment,
user_id varchar(100) not null unique,
user_pw varchar(100) not null,
user_autologin int not null check(user_autologin in(0, 1)),
user_nick_name varchar(100) not null unique
);

create table board_table(
board_idx int not null primary key auto_increment,
board_name varchar(100) not null unique
);

insert into board_table (board_name) values ("κ²μν1");
insert into board_table (board_name) values ("κ²μν2");
insert into board_table (board_name) values ("κ²μν3");
insert into board_table (board_name) values ("κ²μν4");

create table content_table(
content_idx int not null primary key auto_increment,
content_board_idx int not null references board_table(board_idx),
content_writer_idx int not null references user_table(user_idx),
content_subject varchar(500) not null,
content_write_date datetime not null,
content_text longtext not null,
content_image varchar(500)
);

commit;
```

## π¦ 45κ°. μ΄ν΄λ¦½μ€ μ€μ 

### βΆοΈ μ΄ν΄λ¦½μ€ μ€μ 

- μλ² νλ‘κ·Έλ¨ κ΅¬νμ μν΄ μ¬μ©ν  Eclipse κΈ°λ³Έ μ€μ  μν
- Apache-Tomcat μλ²μμ μ°λ μ€μ μ μν
- νλ‘μ νΈλ₯Ό μμ±νκ³  μ€ν νμ€νΈλ₯Ό μν

## π¦ 46κ°. OkHttp λΌμ΄λΈλ¬λ¦¬ μ¬μ©

### βΆοΈ OkHttp λΌμ΄λΈλ¬λ¦¬

- REST API, HTTP ν΅μ μ κ°νΈνκ² κ΅¬νν  μ μλλ‘ λ€μν κΈ°λ₯ μ κ³΅νλ λΌμ΄λΈλ¬λ¦¬

### **π§ μ¬μ©μ μν μΈν**

**1) λ·° λ°μΈλ© μ€μ **

- Module μμ€μ build.gradle νμΌμ viewBinding μ€μ  true μ€λ€.

```php
buildFeatures{
viewBinding = true
}
```

**2) OkHttpλΌμ΄λΈλ¬λ¦¬ μ¬μ©μ μν΄ dependenciesμ μμ‘΄ μΆκ°νλ€.**

```php
implementation 'com.squareup.okhttp3:okhttp:4.9.0'
```

**3) λ€νΈμν¬ μ¬μ©μ μν΄ βμΈν°λ· κΆνβμ μΆκ°νλ€.**

βΎ AndroidManifest.xml 

`<uses-permission android:name = "android.permission.INTERNET"/>`

**4) AndroidManifest.xml μ λ€μμ μΆκ°**

- Http μ¬μ© μ, λ³΄μ λ¬Έμ  λλ¬Έμ λ€μμ μΆκ°νλ€.

`android:usesCleartextTraffic="true"`

**5) λ€νΈμν¬ κ΄λ ¨ μ²λ¦¬λ λ°λμ βμ°λ λβλ‘ λμ μ²λ¦¬ νμ**

βΎ MainActivity.kt 

```kotlin
package com.example.okhttpapplication

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import com.example.okhttpapplication.databinding.ActivityMainBinding
import okhttp3.OkHttpClient
import okhttp3.Request
import kotlin.concurrent.thread

class MainActivity : AppCompatActivity() { //'λ©μΈ' μ‘ν°λΉν°

    //λ·° λ°μΈλ© μ€μ 
    lateinit var mainActivityBinding : ActivityMainBinding

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        //λ·° λ°μΈλ© μ€μ 
        mainActivityBinding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(mainActivityBinding.root)
        //λ²νΌ μ΄λ²€νΈ μ²λ¦¬
        mainActivityBinding.connectBtn.setOnClickListener{
thread{//μ°λ λλ‘ λμν΄μΌ λ€νΈμν¬ κ΄λ ¨ μ²λ¦¬ κ°λ₯
               //localhost λΆλΆμ μλ² Ip μ£Όμ λ΄κΈ°
               val site = "http://172.30.1.9:8080/App3_CommunityServer/test.jsp"

               //okHttp κ°μ²΄
               val client = OkHttpClient()

               val request = Request.Builder().url(site).get().build()
               val response = client.newCall(request).execute() //μ μλ¨

               // λ§μ½ μλ²μ ν΅μ  μ±κ³΅ μ
               if(response.isSuccessful == true) {
                   val result = response.body?.string() //μλ²λ‘λΆν° λ°μ λ°μ΄ν°λ₯Ό λ°μμ¬ μ μλ€.
                   runOnUiThread{
mainActivityBinding.resultText.text= result
}
}
}
        }
}
}
```

**β μ¬κΈ°μ μλ² μ°λν  site μ£Όμ μ localhostλ μμ μ μ»΄ν¨ν° ip μ£Όμλ‘ λμ²΄ν΄μΌ νλ€.**

**β λͺλ Ή νλ‘¬ν¬νΈμμ ipconfig λͺλ Ήμ΄ μλ ₯ μ λ±μ₯νλ ip μ£Όμ κ°μ Έμ¬ κ²** 

![λͺλ Ή μμνΌ μ£Όμ.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eee5614a-0871-4cea-aa89-0e6e61215531/%EB%AA%85%EB%A0%B9_%EC%95%84%EC%9E%89%ED%94%BC_%EC%A3%BC%EC%86%8C.png)

### **π§ μ΅μ’ λͺ¨μ΅**

**1) μλ² μμ μ¬λΌκ° test.jsp νμΌ μ λ΄μ©λ¬Ό**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/99bc964a-f571-4ccb-8641-f3ffbaf9a885/Untitled.png)

**2) μ url μ£Όμμ ipμ£Όμ νΌν©μμΌμ βμλλ‘μ΄λ μ±βμ λ°μ΄ν° κ°μ Έμ΄**

- μ¬μ©μκ° λ²νΌ ν΄λ¦­ μ, κ°μ Έμ¬ μ μλλ‘ μ΄λ²€νΈ μ²λ¦¬λμ΄ μλ€.
