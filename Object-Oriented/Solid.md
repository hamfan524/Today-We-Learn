# ๐ฆฎSolid ์์น๐ฆฎ
>ํ๋ก๊ทธ๋๋จธ๊ฐ ์๊ฐ์ด ์ง๋๋ ์ ์ง ๋ณด์์ ํ์ฅ์ด ์ฌ์ด ์ํํธ์จ์ด๋ฅผ ๋ง๋๋ ๊ฒ์ ์ ์ฉํ๋ 5๊ฐ์ง ์์น

## โจ์ข๋ฅ
1. [SRP](#srpsingle-responsibility-principle)
2. [OCP](#ocpopen-close-principle)
3. [LSP](#lspliskov-substitution-principle)
4. [ISP](#ispinterface-segregation-principle)
5. [DIP](#dipdependency-inversion-principle)

## ๐ปSRP(Single-Responsibility Principle)๐ป
>๋จ์ผ ์ฑ์ ์์น - ์ํํธ์จ์ด ์์(ํด๋์ค, ๋ชจ๋, ํจ์ ๋ฑ)์ ๋จ ํ๋์ ์ฑ์๋ง์ ๊ฐ์ ธ์ผ ํ๋ค.<br>
ํด๋์ค๋ฅผ ๋ณ๊ฒฝํด์ผ ํ๋ ์ด์ ๋ ๋จ์ง ์์ง๋ ํ๋์ฌ์ผ๋ง ํ๋ค.<br>
**์ฑ์**์ **๋ณ๊ฒฝ์ ์ด์ **๋ค.
>* ๋ณ๊ฒฝ์ ์ํด ์์ ์ด ๋๋ ค๋ฉด ๋ง์ ๋ด์ฉ์ด ์์  ๋์ด์ผ ํจ โ ์์ง๋๊ฐ ๋์
>* ๋ณ๊ฒฝ์ ์ํ ์ด์ ๊ฐ ๊ฐ์ ๊ฒ๋ค๋ผ๋ฆฌ ๋ชจ์ด์
>* ์์ ์ ํ๊ณณ์ ์ง์ค๋์ด์ผ ํจ โ ์ฌ๋ฌ ๊ณณ์ ๊ฑธ์น ์์ ์ด ์์ด๋ฃจ์ด์ง โ ๊ฒฐํฉ๋๊ฐ ๋ฎ์

>SRP๋ฅผ ์ ์ฉํ๋ฉด ๊ฐ ํด๋์ค์ ์ฑ์ ์์ญ์ด ํ์คํด์ง๊ธฐ ๋๋ฌธ์ ํ ์ฑ์์ ๋ณ๊ฒฝ์์<br>๋ค๋ฅธ ์ฑ์์ผ๋ก์ ๋ณ๊ฒฝ์ด ์์ ๋ก์ ์ง ์ ์๊ณ 
>์ฑ์์ ์ ์ ํ ๋ถ๋ฐฐํจ์ผ๋ก์จ ์ฝ๋์ ๊ฐ๋์ฑ ํฅ์, ์ ์ง ๋ณด์๊ฐ ์ฉ์ดํด์ง๋ค.

### ๐ ์์ 

![srpแแจแแฆ1](https://user-images.githubusercontent.com/37105602/211811882-9ffd8662-f014-44e2-bc6b-2caf82da3dc4.png)

์์ ๊ฐ์ ๊ด๊ณ์์  ํ๊ธธ๋ ํด๋์ค๊ฐ ๋๋ฌด ๋ง์ ์ฑ์์ ์ํํ๊ณ  ์์ผ๋ฉฐ<br>
ํน์  ๊ธฐ๋ฅ์ ๋ณ๊ฒฝํด์ผ ํ๋ฉด ํด๋์ค ์ ์ฒด๋ฅผ ์์ ํด์ผ ํ๋ ๋ฒ๊ฑฐ๋ก์์ด ๋ฐ์ํ๋ค.

์ด์ ๋ํด SRP๋ฅผ ์ ์ฉํ์ฌ ๋ํ๋ด๋ฉด<br>

![srpแแจแแฆ2](https://user-images.githubusercontent.com/37105602/211812239-04ca488a-e842-48b3-9736-b2dfd74cbf95.png)

์ด์ฒ๋ผ ์ฌ๋ฌ ํด๋์ค๋ก ๋ถ๋ฆฌํ์ฌ ๋ํ๋ผ ์ ์๋ค.<br>์ ๊ทธ๋ฆผ๊ณผ ๋น๊ตํ์ฌ ์ง๊ด์ ์ผ๋ก ๋ณด๋ฉฐ ์ดํดํ๊ธฐ ํธํด์ก์ผ๋ฉฐ ๊ฐ ํด๋์ค์ ์ ์ง ๋ณด์ ์์๋ ํจ์ฌ ๊ฐ๋จํ๊ฒ ํ  ์ ์์์ด ๋๊ปด์ง๋ค.

## ๐ปOCP(Open-Close Principle)๐ป
>๊ฐ๋ฐฉ-ํ์์ ์์น - ๊ธฐ์กด์ ์ฝ๋๋ฅผ ๋ณ๊ฒฝํ์ง ์๊ณ  ๊ธฐ๋ฅ์ ์์ ํ๊ฑฐ๋ ์ถ๊ฐํ  ์ ์๋๋ก **์ค๊ณํด์ผ ํ๋ค.**
>* **ํ์ฅ์ ์ด๋ ค**์๊ณ  **๋ณ๊ฒฝ์ ๋ซํ**์๋ค.
>* ํ์ฅ์ ํ  ๋๋ ๊ธฐ์กด์ ์ฝ๋๋ฅผ ์ต๋ํ ๊ฑด๋๋ฆฌ์ง ์๊ณ  ํ์ฅํ์
>* ๋ง์ฝ ๊ธฐ์กด์ ์ฝ๋๋ฅผ ์์ ํ๊ฒ ๋๋ฉด ์ฐ์์ ์ธ ์์ ์ ํ์ง ์์ ์ ์๊ฒ ํ์
>* ๊ธฐ์กด ์ฝ๋์ ์์ ์ ๋ฒ๊ทธ ๊ฐ๋ฅ์ฑ์ด ์๊ณ , ๊ทธ๊ฒ์ ํ์คํธ ํด์ผํ๋ค.

### ๐ ์์  - (Swift)
```Swift
protocol ๋ํ {
  var ๋๋ : Double { get }
  
  func ๊ทธ๋ฆฌ๊ธฐ()
}

struct ์ผ๊ฐํ: ๋ํ {
  private let ๋ณ: Double
  var ๋๋ : Double { ๋ณ * 3 }
  
  func ๊ทธ๋ฆฌ๊ธฐ() {
    print("๐บ")
  }
}

struct ์ค๊ฐํ: ๋ํ {
  private let ๋ณ: Double
  var ๋๋ : Double { ๋ณ * 4 }
  
  func ๊ทธ๋ฆฌ๊ธฐ() {
    print("๐ง")
  }
}

struct ์ค๊ฐํ: ๋ํ {
  private let ๋ณ: Double
  var ๋๋ : Double { ๋ณ * 5 }
  
  func ๊ทธ๋ฆฌ๊ธฐ() {
    print("โฌ")
  }
}
```
์ ์ถ์ํ๋ฅผ ํ์ฉํ ์ฝ๋์์ ๋ํ(protocol)์ ๋์ด ๋ณ์๋ฅผ ์ถ๊ฐํ๋ค๋ฉด ์ด๋ป๊ฒ ๋๋์ง ์๊ฐํด๋ณด์.

```Swift
var ๋์ด: Double { get }
```
protocol์๋ ๊ฐ๋ณ๊ฒ  ์์ ์ฝ๋ 1์ค๋ง ์์ฑํ๋ฉด ๋์ง๋ง

์ผ๊ฐํ, ์ฌ๊ฐํ, ์ค๊ฐํ ๊ฐ๊ฐ์ ๊ตฌ์กฐ์ฒด์ ๋์ด ๋ณ์๋ฅผ **์ถ๊ฐ/์ฐ์์ ์ธ ์์ ์ ํด์ผ ํ๋ ์ฝ๋์ด๋ค.**

๋ค๋ฅธ ์ฝ๋๋ฅผ ์์๋ก ํ์ธํด ๋ณด์
```Swift
enum ๋ํ {
  case ์ผ๊ฐํ(๋ณ: Double)
  case ์ฌ๊ฐํ(๋ณ: Double)
  case ์ค๊ฐํ(๋ณ: Double)
  
  var ๋๋ : Double {
    switch self {
    case .์ผ๊ฐํ(let ๋ณ): return ๋ณ * 3
    case .์ฌ๊ฐํ(let ๋ณ): return ๋ณ * 4
    case .์ค๊ฐํ(let ๋ณ): return ๋ณ * 5
    }
  }
  
  func ๊ทธ๋ฆฌ๊ธฐ(){
    switch self {
    case .์ผ๊ฐํ: print("๐บ")
    case .์ฌ๊ฐํ: print("๐ง")
    case .์ค๊ฐํ: print("โฌ")
    }
  }
}
```
์ด๋ ๊ฒ ์์ฑ๋ ์ฝ๋๋ ๋์ด ๋ณ์๋ฅผ ์ถ๊ฐํ  ๋, ๋ค๋ฅธ ์ฐ์์ ์ธ ์์ ์ด ํ์ ์์ด

```Swift
  var ๋์ด: Double {
    switch self {
    case .์ผ๊ฐํ(let ๋ณ): return ๋ณ * ๋ณ / 2
    case .์ฌ๊ฐํ(let ๋ณ): return ๋ณ * ๋ณ
    case .์ค๊ฐํ(let ๋ณ): return ๋ณ * ๋ณ * sqrt(25 + 10 * sqrt(5))
    }
  }
```
์ด ๋ถ๋ถ๋ง ์ถ๊ฐํด์ฃผ๋ฉด ํด๊ฒฐ์ด ๋๋ค.<br>
**์ค์ํ ๊ฑด ์ฝ๋์ ์ ๋ต์ ์๋ค**<br>
๋ง์ฝ ๋์ด ๋ณ์๋ฅผ ์ถ๊ฐํ๋๊ฒ ์๋ ์ก๊ฐํ์ด๋ผ๋ ๋ํ์ ์ถ๊ฐํด์ผํ๋ ์์ ์ด ์๊ตฌ๋๋ค๋ฉด
์์ ์ถ์ํ๋ฅผ ํ์ฉํ์ฌ Protocol๋ก ์์ฑ๋ ์ฝ๋๋
```Swift
struct ์ก๊ฐํ: ๋ํ{
  private let ๋ณ: Double
  var ๋๋ : Double { ๋ณ * 3 }
  
  func ๊ทธ๋ฆฌ๊ธฐ() {
    print("โฌข")
  }
}
```
์ด ์ฝ๋๋ง ์ถ๊ฐํ๋ฉด ๋์ง๋ง ์ด๊ฑฐํ(Enum)์ผ๋ก ์์ฑ๋ ์ฝ๋๋ ๊ธฐ์กด์ ์ฝ๋๋ฅผ ๋ณ๊ฒฝ์์ผ์ผํ๋, OCP์์น์ ์งํค์ง ์๋ ์ํฉ์ด ๋๋ค.

**๊ธฐ์กด์ ์ฝ๋๋ฅผ ๋ณ๊ฒฝ์ํค์ง ์์ผ๋ฉด์ ๊ธฐ๋ฅ์ ์ถ๊ฐ, ํ์ฅํ  ์ ์๋๋ก ์ค๊ณํด์ผ ํ๋ค๋ ์๋ฏธ์ด๋ค.**

## ๐ปLSP(Liskov Substitution Principle)๐ป
>๋ฆฌ์ค์ฝํ ์นํ ์์น - **์์ ํด๋์ค๋ ๋ถ๋ชจ ํด๋์ค๋ก์จ์ ์ญํ ์ ์๋ฒฝํ ํ  ์ ์์ด์ผ ํ๋ค.**
>* ์๋ธํ์์ (์์๋ฐ์) ๊ธฐ๋ณธ ํ์์ผ๋ก **๋์ฒด ๊ฐ๋ฅ**ํด์ผ ํ๋ค.
>* ์์ ํด๋์ค๋ ๋ถ๋ชจ ํด๋์ค ๋์(์๋ฏธ)๋ฅผ ๋ฐ๊พธ์ง ์๋๋ค. 

๋จ์ํ๊ฒ ํ์ด๋ณด๋ฉด LSP๋ ์ผ๋ฐํ ๊ด๊ณ์ ๋ํ ์ด์ผ๊ธฐ๋ฉฐ ์์ ํด๋์ค๋ ์ต์ํ ์์ ์ ๋ถ๋ชจ ํด๋์ค์์ ๊ฐ๋ฅํ ํ์๋ ์ํํ  ์ ์์ด์ผ ํ๋ค๋ ๋ป์ด๋ค.

### ๐ ์์  

![lspแแจแแฆ](https://user-images.githubusercontent.com/37105602/211830601-1228a280-d515-480b-aca9-0383c0110e0e.png)

์ฆ ๊ณ์ธต๋/์กฐ์ง๋์ฒ๋ผ ๊ตฌํ๋ ํ๋ก๊ทธ๋๋ฐ์ **๋ธ**์ **์๋ฒ์ง**๋ค ์ ๊ฐ์ ๋ผ๋ฆฌ์ ๋ง์ง ์์์ ์ ์ ์๋ค.<br>
๋ถ๋ฅ๋์ ๊ฒฝ์ฐ ํ์์ ์กด์ฌํ๋ ๊ฒ๋ค์ ์์์ ์๋ ๊ฒ๋ค์ด ์ญํ ์ ํ๋๋ฐ ์ ํ ๋ฌธ์ ๊ฐ ์๋ค.

## ๐ปISP(Interface-Segregation Principle)๐ป
>์ธํฐํ์ด์ค ๋ถ๋ฆฌ ์์น - ํ ํด๋์ค๋ ์์ ์ด ์ฌ์ฉํ์ง ์๋ ์ธํฐํ์ด์ค๋ ๊ตฌํํ์ง ๋ง์์ผ ํ๋ค.<br>
>ํ๋์ ์ผ๋ฐ์ ์ธ ์ธํฐํ์ด์ค๋ณด๋ค๋, ์ฌ๋ฌ ๊ฐ์ ๊ตฌ์ฒด์ ์ธ ์ธํฐํ์ด์ค๊ฐ ๋ซ๋ค.
>* ํด๋ผ์ด์ธํธ ๊ฐ์ฒด๋ ์ฌ์ฉํ์ง ์๋ ๋ฉ์๋์ ์์กด ๊ด๊ณ๋ฅผ ๋งบ์ผ๋ฉด ์ ๋๋ค.

์ฆ ์ด๋ค ํด๋์ค๊ฐ ๋ค๋ฅธ ํด๋์ค์ ์ข์ ๋  ๋ ๊ฐ๋ฅํ **์ต์ํ์ ๊ธฐ๋ฅ**๋ง์ ์ฌ์ฉํด์ผ ํ๋ค๋ ๋ป์ด๋ค.

### ๐ ์์  
ISP๋ ๋น์ทํ ๋ชฉํ๋ฅผ ์ง๋ [SRP(๋จ์ผ ์ฑ์ ์์น)](#srpsingle-responsibility-principle)์ ๋น๊ตํ  ์ ์๋๋ฐ<br>
SRP์ ๊ฒฝ์ฐ ์ฌ์ฉ์์ ์๊ตฌ์ฌํญ์ด๋ ์ทจํฅ์ ๋ฐ๋ผ **ํ๋์ ํด๋์ค**๋ฅผ<br> ํ๋์ ์ฑ์(์ญํ )๋ง ํํ๋ **๋ค์์ ํด๋์ค**๋ก ๋ถํ  ํ๋ ๊ฒ์ด๋ผ๋ฉด
![ispแแจแแฆ](https://user-images.githubusercontent.com/37105602/211834444-bce35732-1163-4e1b-9021-4c52e00f95bc.png)

ISP์ ๊ฒฝ์ฐ <br>
ํ ํด๋์ค๊ฐ ์ฌ๋ฌ ์ญํ ์ ๊ฐ๋ ๊ฒ์ ์ธ์ ํ์ง๋ง ์ด๋ฅผ ๊ตฌํํ๋ ๊ฒ์ ํด๋์ค๊ฐ ์๋<br>
๊ฐ ์ธํฐํ์ด์ค๋ณ๋ก ๋๋์ด ์ฌ์ฉ์์ ํนํ๋ ์ธํฐํ์ด์ค๋ก ์ฑ์์ ๋ถ๋ฆฌํ๋ ๋ฐฉ์์ด๋ค.

>### ISP๋ฅผ ์๋ฐํ์์ ๋ ์๊ธฐ๋ ๋ฌธ์ 
>์ฌ์ฉํ์ง ์์ง๋ง ์์กด์ฑ์ ๊ฐ์ง ํด๋์ค๋ฅผ ๊ฐ์ง๊ณ  ์์ผ๋ฉด ํ ๊ธฐ๋ฅ์ ๋ณ๊ฒฝ์ด ๋ฐ์ํ๊ณ  ๋ค๋ฅธ ๊ธฐ๋ฅ์ ์ฌ์ฉํ๋ ํด๋ผ์ด์ธํธ๋ค์๊ฒ๋ ์ํฅ์ ๋ฏธ์น๊ฒ ๋๋ค.
๋ฐ๋ผ์ ์ฌ์ฉํ๋ ๊ธฐ๋ฅ๋ง ์ ๊ณตํ๋๋ก ์ธํฐํ์ด์ค๋ฅผ ๋ถ๋ฆฌํจ์ผ๋ก์จ ๊ธฐ๋ฅ์ ๋ํ ์ฌํ๋ฅผ ์ต์ํ ํด์ผํ๋ค.

## ๐ปDIP(Dependency-Inversion Principle)๐ป
>์์กด ์ญ์  ์์น
>* ์์๋ ๋ฒจ ๋ชจ๋์ ํ์๋ ๋ฒจ ๋ชจ๋์ ์์กดํ๋ฉด ์๋๋ค. (๋ ๋ค ์ถ์ํ๋ ์ธํฐํ์ด์ค์ ์์กดํด์ผ ํ๋ค)
>* ์ถ์ํ๋ ๊ตฌ์ฒดํ์ ์์กดํ๋ฉด ์๋๊ณ , ๊ตฌ์ฒดํ๋ ์ถ์ํ์ ์์กดํ๋ฉด ์๋๋ค.
>* ์์ฃผ ๋ณ๊ฒฝ๋๋ ๊ตฌ์ฒด(Concrete) ํด๋์ค์ ์์กดํ๋ฉด ์๋๋ค.

์์กด ๊ด๊ณ๋ฅผ ๋งบ์ ๋, ๋ณํํ๊ธฐ ์ฌ์ด๊ฒ ๋ณด๋จ **๋ณํํ๊ธฐ ์ด๋ ค์ด ๊ฒ(๊ฑฐ์ ๋ณํ๊ฐ ์๋ ๊ฒ)์ ์์กดํด์ผ ํ๋ค๋ ์์น**์ด๋ค.


### ๐ ์์  

![dipแแจแแฆ](https://user-images.githubusercontent.com/37105602/211841155-dcadffbf-f6ca-49a3-ae57-691e300ab725.png)
DIP ์ ์ฉ ์  ๊ทธ๋ฆผ์์๋ ์๋ฉ,๋ผ๋ผ ๋ฑ ํด๋์ค๋ค์ด ๊ทธ ๋ฌด์์๋ ์์กดํ์ง ์๋ ์ํ์๋๋ฐ<br>
์ ์ฉ ํ ์ปคํผ๋ผ๋ ์ถ์์ ์ธ ์ธํฐํ์ด์ค๋ฅผ ์์กดํ๊ฒ ๋๋ค. ์ฆ ์์กด ์ญ์ ์ด ์ผ์ด๋ ๊ฒ์ด๋ค.

๋ํ ์ง์ฅ์ธ๋ ๋ณํํ๊ธฐ ์ฌ์ด ๊ตฌ์ฒด์ ์ธ ๊ฒ์ ์์กดํ๋ ์ํ์์ ์ถ์ํ๋ ๊ฒ์ ์์กดํจ์ผ๋ก์จ<br>
๋ณํ์ ์ํฅ์ ๋ฐ์ง ์๊ฒ ๋ ์์กด ์ญ์ ์ด ๋ฐ์ํ์ฌ ๊ด๊ณ๊ฐ ๋งค์ฐ ํผํผํด์ก๋ค.
>DIP ์์กด์ฑ ์ฃผ์์ ๊ฒฐ๊ตญ [OCP(๊ฐ๋ฐฉํ์์ ์์น)](#ocpopen-close-principle)์๋ ์ฐ๊ฒฐ๋์ด ์๋ค.

## โจ๋ง๋ฌด๋ฆฌ
๊ฐ์ฒด์งํฅ ์ค๊ณ ์์น๋ค์ ๊ฒฐ๊ตญ ์ถ์ํ๋ฅผ ์ด๋ป๊ฒ ์ด์ฉํ์ฌ ์ค๊ณํ ์ง๋ฅผ 5๊ฐ์ง๋ก ๋๋ ๊ฒ๊ณผ ๊ฐ๋ค๊ณ  ๋ณผ ์ ์๋ค.
