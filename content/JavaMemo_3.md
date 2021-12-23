Title: JavaMemo_2
Date: 2021-12-23
Category: Java
Tags: Java

Java記述のルール  
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

```Java
import 
```

完全修飾詞で読み込むパターン①
```Java
import java.util.ArrayList;
```

完全修飾詞で読み込むパターン②
```Java
java.util.ArrayList<String> list;
```
無名パッケージは無名パッケージに属するクラスしか読み込めない。

```Java

```

ディレクトリ構成がsrc-Main.javaの場合、
package宣言をしないとエラーとなる。  
```Java
class Main {
    public static void main(String[] args) {
        java.util.ArrayList<String> list2;
    }
}
```

```Java
The declared package "" does not match the expected package "src"
```

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

compile 指定した場所にclassファイルを生成
```Java
// srcフォルダに生成 command option directory Main.java
javac -sourcepath src src/Main.java
```

実行
```Java 
java src/Main
```

指定した場所にjarを生成
```Java
jar -cvf src/Main.jar src/*.class
```