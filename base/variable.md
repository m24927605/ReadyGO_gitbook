**2-0 變數**
> Golang宣告變數比較特別一點，型別寫在變數後面。  

Golang有25個保留字，不能做為變數名稱使用，如下列：  
> break default func interface select
> case defer go map struct
> chan else goto package switch
> const fallthrough if range type
> continue for import return var

下列幾種是預先宣告，可以重新宣告：
> 常數：true false iota nil  
> 型別：int int8 int16 int32 int64  
> &emsp;&emsp;&emsp;uint uint8 uint16 uint32 uint64  
> &emsp;&emsp;&emsp;float32 float64 complex128 complex64  
> &emsp;&emsp;&emsp;bool byte rune string error  
> 函式：make len cap new append copy close delete  
> &emsp;&emsp;&emsp;complex real imag panic recover

Golang常見有四種宣告：var、const、type、func
> var作為宣告變數使用，給定變數名稱。  
> const作為宣告常數使用，常數是指不會被改變的值。  
> type作為宣告型別使用。  
> func作為宣告函式使用。  

宣告範例程式碼：
```
package main

import (
	"fmt"     //可以印出結果的套件
	"reflect" //可以檢查型別的套件
)

func main() {
	var name string = "Michael"
	var i, j, k int                   //型別預期是 int int int
	var a, b, c = false, 87.87, "wow" //型別預期是 bool float64 string
	m := 87                           //型別預期是 int  請見2-1說明
	n := new(int)                     //型別預期是 *int 請見2-2說明
	fmt.Println("值:", name, "型別：", reflect.TypeOf(name))
	fmt.Println("值:", i, j, k, "型別：", reflect.TypeOf(i), reflect.TypeOf(j), reflect.TypeOf(k))
	fmt.Println("值:", a, b, c, "型別：", reflect.TypeOf(a), reflect.TypeOf(b), reflect.TypeOf(c))
	fmt.Println("值:", m, "型別：", reflect.TypeOf(m))
	fmt.Println("值:", n, "型別：", reflect.TypeOf(n))

	type newType string
	var who newType = "Michael" //型別預期是 string 請見2-4說明
	fmt.Println("值:", who, "型別：", reflect.TypeOf(who))
}
```
結果：
<pre><font color="#8AE234"><b>$</b></font><b> </b>go run var_01.go
值: Michael 型別： string
值: 0 0 0 型別： int int int
值: false 87.87 wow 型別： bool float64 string
值: 87 型別： int
值: 0xc0000120f8 型別： *int
值: Michael 型別： main.newType
</pre>

**2-1 短變數宣告**
> 型別由值定義。

```
m := 87 //int
```

**2-2 new 建構函式**
> 變數若是由new(T)方式宣告，其型別為 *T型別，其值為 *T型別的位址值(可參考2-3)。  

```
n:=new(int)  //n指向不具名的int變數
```

**2-3 指標**
> 指標是變數的位址，每個變數都會有位址，但每個值可不一定有，我們可以透過改變指標的值去改變變數的值。

```
x:= 10
y:= &x //y的型別為*int且指向x，*int念做point to int
*y = 20 //x也會為20
```

**2-4 型別宣告** 
> 可以自定義型別。   

```
type newType string
var who newType = "Michael"  // who的型別會是main.newType

```