Title: JavaMemo_2
Date: 2021-12-23
Category: Java
Tags: Java

## Java記述のルール  
package宣言  
import宣言
class  
順番が異なるとコンパイルエラーとなる。  

```Java
package src;
import java.util.*;

class Main {
    public static void main(String[] args) {
    }
}
```

*をつけると、指定したpackageに属するクラスを全て使用できる。  
```Java
package src;
import java.util.*;

class Main {
    public static void main(String[] args) {
        ArrayList<String> list1;
    }
}
```

完全修飾詞で読み込むパターン①  
import宣言  
```Java
import java.util.ArrayList;
```

完全修飾詞で読み込むパターン②  
宣言時に完全修飾詞を追記  
```Java
java.util.ArrayList<String> list;
```

 ## 別のpackageの読み込み

2つの有名packageと1つの無名package
```Java
src/Main.java
sample/Sample.java
Sample.java
```
### src/Main.java  
別のpackageのクラスを読み込む場合はimportする
src/Main.java
```Java
package src;
// samplepackageを読み込む
import sample.Sample;

public class Main {
    public static void main(String[] args) {
        System.out.println(1);

        new Sample();
    }
}
```

### sample/Sample.java
```
package sample;

public class Sample {
    public void sample(){
        System.out.println("sample");
    }
}
```

無名パッケージは無名パッケージに属するクラスしか読み込めない。 
### sample.java
```Java
public class Sample {
    public void sample(){
        System.out.println("sample");
    }
}
```
## packageの注意点  
ディレクトリ構成がsrc/Main.javaの場合、
package宣言をしないとエラーとなる。  
```Java
class Main {
    public static void main(String[] args) {
    }
}
```

```Java
The declared package "" does not match the expected package "src"
```

## javaのcommand
java commandでの呼び出し
```Java
java Main.java
```

sourceファイルモードでの呼び出し  
class名とファイル名が異なっている場合でも呼び出せる様になる。  
```Java
// ファイル名Main.javaをMainに変更
mv Main.java Main
java --source 17  Main
```

```Java
// 元に戻す。
mv Main Main.java
```

## classファイルを作成後、jarを作成し。jarを起動してみる
ソースコード  
```Java
package src;

public class Main {
    public static void main(String[] args) {
        System.out.println(1);
    }
}
```

指定した場所にclassファイルを生成
```Java
// compile後に、classファイルが作成される
javac -sourcepath src src/Main.java
```

classファイルを実行
```Java 
java src/Main
```

指定した場所にjarを生成
```Java
jar -cvf src/Main.jar src/*.class
```

manifestファイルが存在しない状態でjarを起動した場合  
```Java
no main manifest attribute, in src/Main.jar
```

manifestファイルを作成
```Java
touch Main.mf
```
manifestファイルに以下記述  
起動するための情報が必要となる  
```Java
Main-Class: src.Main
```

manifestファイルをjarに追加する
```Java
jar -cvfm src/Main.jar src/Main.mf src/*.class
```

```Java
added manifest
adding: src/Main.class(in = 382) (out= 272)(deflated 28%)
```

jarを起動する
```Java
java -jar src/Main.jar
```
jarの中身を確認
```Java
jar -tf src/Main.jar
```

```java
META-INF/
META-INF/MANIFEST.MF
src/Main.class
```

jarを展開する  
カレントディレクトリに展開されるので場所には注意が必要    
```Java
jar -xvf src/Main.jar
```

```Java
  created: META-INF/
 inflated: META-INF/MANIFEST.MF
 inflated: src/Main.class
```