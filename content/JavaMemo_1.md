Title: JavaMemo_1
Date: 2021-12-22
Category: Java
Tags: Java

# 数値処理

```Java
import java.lang.Math
```

### 数値の累乗

```Java
// 第一引数に累乗したい数値、第二引数に累乗する回数
double num = Math.pow(2,3);
```

```Java
// 戻り値はdouble型
8.0
```

### 平方根

```Java 
double num1 = Math.sqrt(4);

double num2 = Math.sqrt(-1);
```

```Java
// 平方根を返す 
2
//　負数の場合  
NaN
```

### 四捨五入
```Java
// 引数がfloat 
int num1 = Math.round((float)4.49);
// 引数がdouble　
long num2 = Math.round((double)4.49);
```

```Java
// 戻り値はint
4
// 戻り値はlong
4
```

### 切り上げ
```Java
double num1 = Math.ceil(4.5);
        
double num2 = Math.ceil(3.1);
```

```Java
// 戻り値はdouble
4.0
// 戻り値はdouble
3.0
```


# リストの宣言と初期化
```Java
import java.util.ArraysList;
import java.util.Arrays;
import java.util.List;
```

```Java
// 可変長　削除・追加可能
ArrayList<Integer> array1 = new ArrayList<Integer>(){
    {
        add(1);
        add(2);
        add(3);
    }
};

// 可変長　削除・追加可能
ArrayList<Integer> array2 = new ArrayList<Integer>(Arrays.asList(1,2,3));
        
// 固定長　削除・追加不可 java.lang.UnsupportedOperationException
List<Integer> array3 = Arrays.asList(1,2,3);
```

```Java
[1, 2, 3]
[1, 2, 3]
[1, 2, 3]
```


