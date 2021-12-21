Title: JavaMemo_2
Date: 2021-12-21
Category: Java
Tags: Java

## Javaのエントリーポイント  
public static void main  
引数がStringの配列、可変長数であること  
```Java
public class Main {
    public static void main(String[] args) {
        System.out.println(args.length));
    }
}
```

```Java
// 実行時に配列インスタンスが生成されるためlength0となる。
// argsだと、ハッシュコード
0
```
## 例外の基本形  
catchは複数記述できるが、それ以外を複数記述するとコンパイルエラーとなる。  
try,catch,finallyの順番も守る必要がある。  
```Java
try{
    // 処理
}catch(Exception e){
    // 例外発生時の処理
}finally{
    // 必ず実行したい処理
}
```

finally複数のためコンパイルエラー
```Java
try{
    
}catch(Exception e){
    
}finally{
    
}finally{
            
}
```

記述の順番が不正なためコンパイルエラー
```Java
try{
    
}finally{
    
}catch(Exception e){
    
}
```

catchの省略  
```Java
try{
    System.out.println("A");
}finally{
    System.out.print("B");
}
```

```Java
A
B
```

catchを複数記述した際の、継承関係によるコンパイルエラー  
スーパークラスで先に例外をcatchするため、  
サブクラスのRuntimeexceptionは到達不可能コードとなる  
```Java
try{
    System.out.println("A");
}catch(Exception e){
    System.out.println(e);
    // 到達不可能コード
}catch(RuntimeException re){
    System.out.println(re);
}
```

サブクラスを先に記述する  
```Java
try{
    System.out.println("A");
}catch(RuntimeException re){
    System.out.println(re);
}catch(Exception e){
    System.out.println(e);
}
```

```Java
A
```

```Java
try{
    throw new Exception();
}catch(Exception e){
    System.out.println(e);
}
```
