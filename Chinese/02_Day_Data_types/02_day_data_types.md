<div align="center">
  <h1> 30天JavaScript编程挑战：数据类型</h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

  <sub>作者：
  <a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a>
  <small> 2020年1月</small>

  <sub>翻译：
  <a href="https://github.com/DoYoungDo" target="_blank">Doyoung</a>
  <small> 2025年11月</small>

  </sub>
</div>
</div>

[<< 第1天](../readMe.md) | [第3天 >>](../03_Day_Booleans_operators_date/03_booleans_operators_date.md)

![三十天JavaScript编程挑战](../../images/banners/day_1_2.png)

- [📔 第2天](#-day-2)
	- [数据类型](#data-types)
		- [基本数据类型](#primitive-data-types)
		- [非基本数据类型](#non-primitive-data-types)
	- [数字](#numbers)
		- [声明数字数据类型](#declaring-number-data-types)
		- [Math对象](#math-object)
			- [随机数生成器](#random-number-generator)
	- [字符串](#strings)
		- [字符串连接](#string-concatenation)
			- [使用加法运算符连接](#concatenating-using-addition-operator)
			- [长文本字符串](#long-literal-strings)
			- [字符串中的转义序列](#escape-sequences-in-strings)
			- [模板字面量（模板字符串）](#template-literals-template-strings)
		- [字符串方法](#string-methods)
	- [检查数据类型和类型转换](#checking-data-types-and-casting)
		- [检查数据类型](#checking-data-types)
		- [改变数据类型（类型转换）](#changing-data-type-casting)
			- [字符串转整数](#string-to-int)
			- [字符串转浮点数](#string-to-float)
			- [浮点数转整数](#float-to-int)
	- [💻 第2天：练习](#-day-2-exercises)
		- [练习：级别 1](#exercise-level-1)
		- [练习：级别 2](#exercise-level-2)
		- [练习：级别 3](#exercises-level-3)

# 📔 第二天 {#-day-2}

## 数据类型 {#data-types}

在前面的章节中，我们稍微提到了数据类型。数据或值都有数据类型。数据类型描述了数据的特征。数据类型可以分为两种：

1. 基本数据类型
2. 非基本数据类型（对象引用）

### 基本数据类型 {#primitive-data-types}

JavaScript 中的基本数据类型包括：

 1. Numbers（数字） - 整数、浮点数
 2. Strings（字符串） - 单引号、双引号或反引号下的任何数据
 3. Booleans（布尔值） - true 或 false 值
 4. Null（空值） - 空值或无值
 5. Undefined（未定义） - 已声明但没有值的变量
 6. Symbol（符号） - 可以通过 Symbol 构造函数生成的唯一值

JavaScript 中的非基本数据类型包括：

1. 对象
2. 数组

现在，让我们看看基本数据类型和非基本数据类型到底是什么意思。
*基本*数据类型是不可变（不可修改）的数据类型。一旦创建了基本数据类型，我们就无法修改它。

**示例：**

```js
let word = 'JavaScript'
```

如果我们尝试修改变量 *word* 中存储的字符串，JavaScript 应该会报错。任何在单引号、双引号或反引号下的数据类型都是字符串数据类型。

```js
word[0] = 'Y'
```

这个表达式不会改变变量 *word* 中存储的字符串。因此，我们可以说字符串是不可修改的，或者说不可变。
基本数据类型通过其值进行比较。让我们比较不同的数据值。参见下面的示例：

```js
let numOne = 3
let numTwo = 3

console.log(numOne == numTwo)      // true

let js = 'JavaScript'
let py = 'Python'

console.log(js == py)             //false 

let lightOn = true
let lightOff = false

console.log(lightOn == lightOff) // false
```

### 非基本数据类型 {#non-primitive-data-types}

*非基本*数据类型是可修改的或可变的。我们可以在创建非基本数据类型后修改其值。
让我们通过创建一个数组来看看。数组是方括号中的数据值列表。数组可以包含相同或不同的数据类型。数组值通过其索引引用。在 JavaScript 中，数组索引从零开始。也就是说，数组的第一个元素位于索引零，第二个元素位于索引一，第三个元素位于索引二，等等。

```js
let nums = [1, 2, 3]
nums[0] = 10

console.log(nums)  // [10, 2, 3]
```

如你所见，数组是非基本数据类型，是可变的。非基本数据类型不能通过值进行比较。即使两个非基本数据类型具有相同的属性和值，它们也不是严格相等的。

```js
let nums = [1, 2, 3]
let numbers = [1, 2, 3]

console.log(nums == numbers)  // false

let userOne = {
name:'Asabeneh',
role:'teaching',
country:'Finland'
}

let userTwo = {
name:'Asabeneh',
role:'teaching',
country:'Finland'
}

console.log(userOne == userTwo) // false
```

经验法则，我们不比较非基本数据类型。不要比较数组、函数或对象。
非基本值被称为引用类型，因为它们通过引用而不是值进行比较。只有当两个对象引用同一个底层对象时，它们才是严格相等的。

```js
let nums = [1, 2, 3]
let numbers = nums

console.log(nums == numbers)  // true

let userOne = {
name:'Asabeneh',
role:'teaching',
country:'Finland'
}

let userTwo = userOne

console.log(userOne == userTwo)  // true
```

如果你觉得很难理解基本数据类型和非基本数据类型之间的区别，你不是唯一一个。冷静下来，继续下一节，过段时间再回来。现在让我们从数字类型开始数据类型。

## 数字 {#numbers}

数字是可以进行所有算术运算的整数和小数值。
让我们看一些数字的示例。

### 声明数字数据类型 {#declaring-number-data-types}

```js
let age = 35
const gravity = 9.81  // 我们对不变化的值使用 const，重力常数，单位 m/s²
let mass = 72         // 质量，单位千克
const PI = 3.14       // 圆周率，一个几何常数

// 更多示例
const boilingPoint = 100 // 温度，单位°C，水的沸点，这是一个常数
const bodyTemp = 37      // °C，人体平均温度，这是一个常数

console.log(age, gravity, mass, PI, boilingPoint, bodyTemp)
```

### Math 对象 {#math-object}

在 JavaScript 中，Math 对象提供了许多处理数字的方法。

```js
const PI = Math.PI

console.log(PI)                            // 3.141592653589793

// 四舍五入到最接近的数字
// 如果大于 0.5 则向上舍入，如果小于 0.5 则向下舍入

console.log(Math.round(PI))                // 3，将值四舍五入到最接近的数字

console.log(Math.round(9.81))              // 10

console.log(Math.floor(PI))                // 3，向下舍入

console.log(Math.ceil(PI))                 // 4，向上舍入

console.log(Math.min(-5, 3, 20, 4, 5, 10)) // -5，返回最小值

console.log(Math.max(-5, 3, 20, 4, 5, 10)) // 20，返回最大值

const randNum = Math.random() // 创建 0 到 0.999999 之间的随机数
console.log(randNum)

// 让我们创建 0 到 10 之间的随机数

const num = Math.floor(Math.random () * 11) // 创建 0 到 10 之间的随机数
console.log(num)

//绝对值
console.log(Math.abs(-10))      // 10

//平方根
console.log(Math.sqrt(100))     // 10

console.log(Math.sqrt(2))       // 1.4142135623730951

// 幂
console.log(Math.pow(3, 2))     // 9

console.log(Math.E)             // 2.718

// 对数
// 返回以 E 为底的 x 的自然对数，Math.log(x)
console.log(Math.log(2))        // 0.6931471805599453
console.log(Math.log(10))       // 2.302585092994046

// 分别返回 2 和 10 的自然对数
console.log(Math.LN2)           // 0.6931471805599453
console.log(Math.LN10)          // 2.302585092994046

// 三角函数
Math.sin(0)
Math.sin(60)

Math.cos(0)
Math.cos(60)
```

#### 随机数生成器 {#random-number-generator}

JavaScript Math 对象有一个 random() 方法数生成器，它生成从 0 到 0.999999999... 的数字。

```js
let randomNum = Math.random() // 生成 0 到 0.999... 的数
```

现在，让我们看看如何使用 random() 方法生成 0 到 10 之间的随机数：

```js
let randomNum = Math.random()         // 生成 0 到 0.999 的数
let numBtnZeroAndTen = randomNum * 11

console.log(numBtnZeroAndTen)         // 这给出：最小 0，最大 10.99

let randomNumRoundToFloor = Math.floor(numBtnZeroAndTen)
console.log(randomNumRoundToFloor)    // 这给出 0 到 10 之间的数
```

## 字符串 {#strings}

字符串是文本，可以用**单引号**、**双引号**或**反引号**包裹。要声明一个字符串，我们需要变量名、赋值运算符，以及用单引号、双引号或反引号包裹的值。
让我们看一些字符串的例子：

```js
let space = ' '           // 一个空字符串
let firstName = 'Asabeneh'
let lastName = 'Yetayeh'
let country = 'Finland'
let city = 'Helsinki'
let language = 'JavaScript'
let job = 'teacher'
let quote = "The saying,'Seeing is Believing' is not correct in 2020."
let quotWithBackTick = `The saying,'Seeing is Believing' is not correct in 2020.`
```


### 字符串连接 {#string-concatenation}

将两个或多个字符串连接在一起称为连接。
使用前面字符串部分声明的字符串：

```js
let fullName = firstName + space + lastName; // 连接，将两个字符串合并在一起
console.log(fullName);
```

```sh
Asabeneh Yetayeh
```

我们可以用不同的方式连接字符串。

#### 使用加法运算符连接 {#concatenating-using-addition-operator}

使用加法运算符连接是一种旧方法。这种连接方式既繁琐又容易出错。了解如何以这种方式连接是好的，但我强烈建议使用ES6模板字符串（后面会解释）。

```js
// 声明不同数据类型的不同变量
let space = ' '
let firstName = 'Asabeneh'
let lastName = 'Yetayeh'
let country = 'Finland'
let city = 'Helsinki'
let language = 'JavaScript'
let job = 'teacher'
let age = 250


let fullName =firstName + space + lastName
let personInfoOne = fullName + '. I am ' + age + '. I live in ' + country; // ES5字符串加法

console.log(personInfoOne)
```

```sh
Asabeneh Yetayeh. I am 250. I live in Finland
```

#### 长文本字符串 {#long-literal-strings}

字符串可以是单个字符、段落或一整页。如果字符串长度太长，无法在一行中显示，我们可以在每行末尾使用反斜杠字符（\）来表示字符串将在下一行继续。
**示例：**

```js
const paragraph = "My name is Asabeneh Yetayeh. I live in Finland, Helsinki.\
I am a teacher and I love teaching. I teach HTML, CSS, JavaScript, React, Redux, \
Node.js, Python, Data Analysis and D3.js for anyone who is interested to learn. \
In the end of 2019, I was thinking to expand my teaching and to reach \
to global audience and I started a Python challenge from November 20 - December 19.\
It was one of the most rewarding and inspiring experience.\
Now, we are in 2020. I am enjoying preparing the 30DaysOfJavaScript challenge and \
I hope you are enjoying too."

console.log(paragraph)
```

#### 字符串中的转义序列 {#escape-sequences-in-strings}

在JavaScript和其他编程语言中，\后跟某些字符是一个转义序列。让我们看看最常见的转义字符：

- \n: 换行
- \t: 制表符，表示8个空格
- \\\\: 反斜杠
- \\': 单引号(')
- \\": 双引号(")
  
```js
console.log('I hope everyone is enjoying the 30 Days Of JavaScript challenge.\nDo you ?') // 换行
console.log('Days\tTopics\tExercises')
console.log('Day 1\t3\t5')
console.log('Day 2\t3\t5')
console.log('Day 3\t3\t5')
console.log('Day 4\t3\t5')
console.log('This is a backslash  symbol (\\)') // 写入反斜杠
console.log('In every programming language it starts with \"Hello, World!\"')
console.log("In every programming language it starts with \'Hello, World!\'")
console.log('The saying \'Seeing is Believing\' isn\'t correct in 2020')
```

控制台输出：

```sh
I hope everyone is enjoying the 30 Days Of JavaScript challenge.
Do you ?
Days  Topics  Exercises
Day 1 3 5
Day 2 3 5
Day 3 3 5
Day 4 3 5
This is a backslash  symbol (\)
In every programming language it starts with "Hello, World!"
In every programming language it starts with 'Hello, World!'
The saying 'Seeing is Believing' isn't correct in 2020
```

#### 模板字面量（模板字符串）{#template-literals-template-strings}

要创建模板字符串，我们使用两个反引号。我们可以在模板字符串内注入数据作为表达式。要注入数据，我们用花括号({})包裹表达式，前面加上$符号。见下面的语法。

```js
//语法
`String literal text`
`String literal text ${expression}`
```

**示例：1**

```js
console.log(`The sum of 2 and 3 is 5`)              // 静态写入数据
let a = 2
let b = 3
console.log(`The sum of ${a} and ${b} is ${a + b}`) // 动态注入数据
```

**示例：2**

```js
let firstName = 'Asabeneh'
let lastName = 'Yetayeh'
let country = 'Finland'
let city = 'Helsinki'
let language = 'JavaScript'
let job = 'teacher'
let age = 250
let fullName = firstName + ' ' + lastName

let personInfoTwo = `I am ${fullName}. I am ${age}. I live in ${country}.` //ES6 - 字符串插值方法
let personInfoThree = `I am ${fullName}. I live in ${city}, ${country}. I am a ${job}. I teach ${language}.`
console.log(personInfoTwo)
console.log(personInfoThree)
```

```sh
I am Asabeneh Yetayeh. I am 250. I live in Finland.
I am Asabeneh Yetayeh. I live in Helsinki, Finland. I am a teacher. I teach JavaScript.
```

使用字符串模板或字符串插值方法，我们可以添加表达式，可以是值，也可以是一些操作（比较、算术运算、三元运算）。

```js
let a = 2
let b = 3
console.log(`${a} is greater than ${b}: ${a > b}`)
```

```sh
2 is greater than 3: false
```

### 字符串方法 {#string-methods}

JavaScript中的一切都是对象。字符串是原始数据类型，这意味着一旦创建我们就无法修改它。字符串对象有许多字符串方法。有不同的字符串方法可以帮助我们处理字符串。

1. *length*: 字符串*length*方法返回字符串中的字符数，包括空格。

**示例：**

```js
let js = 'JavaScript'
console.log(js.length)         // 10
let firstName = 'Asabeneh'
console.log(firstName.length)  // 8
```

2. *访问字符串中的字符*: 我们可以使用索引访问字符串中的每个字符。在编程中，计数从0开始。字符串的第一个索引是零，最后一个索引是字符串长度减一。

  ![Accessing sting by index](../../images/string_indexes.png)
  
让我们访问'JavaScript'字符串中的不同字符。

```js
let string = 'JavaScript'
let firstLetter = string[0]

console.log(firstLetter)           // J

let secondLetter = string[1]       // a
let thirdLetter = string[2]
let lastLetter = string[9]

console.log(lastLetter)            // t

let lastIndex = string.length - 1

console.log(lastIndex)  // 9
console.log(string[lastIndex])    // t
```

3. *toUpperCase()*: 此方法将字符串更改为大写字母。

```js
let string = 'JavaScript'

console.log(string.toUpperCase())     // JAVASCRIPT

let firstName = 'Asabeneh'

console.log(firstName.toUpperCase())  // ASABENEH

let country = 'Finland'

console.log(country.toUpperCase())    // FINLAND
```

4. *toLowerCase()*: 此方法将字符串更改为小写字母。

```js
let string = 'JavasCript'

console.log(string.toLowerCase())     // javascript

let firstName = 'Asabeneh'
console.log(firstName.toLowerCase())  // asabeneh

let country = 'Finland'

console.log(country.toLowerCase())   // finland
```

5. *substr()*: 它接受两个参数，起始索引和要切片的字符数。

```js
let string = 'JavaScript'
console.log(string.substr(4,6))    // Script

let country = 'Finland'
console.log(country.substr(3, 4))   // land
```

6. *substring()*: 它接受两个参数，起始索引和停止索引，但它不包括停止索引处的字符。

```js
let string = 'JavaScript'

console.log(string.substring(0,4))     // Java
console.log(string.substring(4,10))    // Script
console.log(string.substring(4))       // Script

let country = 'Finland'

console.log(country.substring(0, 3))   // Fin
console.log(country.substring(3, 7))   // land
console.log(country.substring(3))      // land
```

7. *split()*: split方法在指定位置分割字符串。

```js
let string = '30 Days Of JavaScript'

console.log(string.split())     // 更改为数组 -> ["30 Days Of JavaScript"]
console.log(string.split(' '))  // 在空格处拆分为数组 -> ["30", "Days", "Of", "JavaScript"]

let firstName = 'Asabeneh'

console.log(firstName.split())    // 更改为数组 - > ["Asabeneh"]
console.log(firstName.split(''))  // 在每个字母处拆分为数组 ->  ["A", "s", "a", "b", "e", "n", "e", "h"]

let countries = 'Finland, Sweden, Norway, Denmark, and Iceland'

console.log(countries.split(','))  // 在逗号处拆分为数组 -> ["Finland", " Sweden", " Norway", " Denmark", " and Iceland"]
console.log(countries.split(', ')) //  ["Finland", "Sweden", "Norway", "Denmark", "and Iceland"]
```

8. *trim()*: 移除字符串开头或结尾的空格。

```js
let string = '   30 Days Of JavaScript   '

console.log(string)
console.log(string.trim(' '))

let firstName = ' Asabeneh '

console.log(firstName)
console.log(firstName.trim())  // 仍然移除字符串开头和结尾的空格
```

```sh
   30 Days Of JavasCript   
30 Days Of JavasCript
  Asabeneh 
Asabeneh
```

9. *includes()*: 它接受一个子字符串参数，并检查子字符串参数是否存在于字符串中。*includes()*返回一个布尔值。如果子字符串存在于字符串中，它返回true，否则返回false。

```js
let string = '30 Days Of JavaScript'

console.log(string.includes('Days'))     // true
console.log(string.includes('days'))     // false - 它是区分大小写的！
console.log(string.includes('Script'))   // true
console.log(string.includes('script'))   // false
console.log(string.includes('java'))     // false
console.log(string.includes('Java'))     // true

let country = 'Finland'

console.log(country.includes('fin'))     // false
console.log(country.includes('Fin'))     // true
console.log(country.includes('land'))    // true
console.log(country.includes('Land'))    // false
```

10. *replace()*: 以旧子字符串和新子字符串作为参数。

```js
string.replace(oldsubstring, newsubstring)
```

```js
let string = '30 Days Of JavaScript'
console.log(string.replace('JavaScript', 'Python')) // 30 Days Of Python

let country = 'Finland'
console.log(country.replace('Fin', 'Noman'))       // Nomanland
```

11. *charAt()*: 接受索引并返回该索引处的值

```js
string.charAt(index)
```

```js
let string = '30 Days Of JavaScript'
console.log(string.charAt(0))        // 3

let lastIndex = string.length - 1
console.log(string.charAt(lastIndex)) // t
```

12. *charCodeAt()*: 接受索引并返回该索引处值的字符代码（ASCII数字）

```js
string.charCodeAt(index)
```

```js
let string = '30 Days Of JavaScript'
console.log(string.charCodeAt(3))        // D ASCII数字是68

let lastIndex = string.length - 1
console.log(string.charCodeAt(lastIndex)) // t ASCII是116

```

13.  *indexOf()*: 接受一个子字符串，如果子字符串存在于字符串中，它返回子字符串的第一个位置，如果不存在则返回-1

```js
string.indexOf(substring)
```

```js
let string = '30 Days Of JavaScript'

console.log(string.indexOf('D'))          // 3
console.log(string.indexOf('Days'))       // 3
console.log(string.indexOf('days'))       // -1
console.log(string.indexOf('a'))          // 4
console.log(string.indexOf('JavaScript')) // 11
console.log(string.indexOf('Script'))     //15
console.log(string.indexOf('script'))     // -1
```

14.  *lastIndexOf()*: 接受一个子字符串，如果子字符串存在于字符串中，它返回子字符串的最后一个位置，如果不存在则返回-1

```js
//语法
string.lastIndexOf(substring)
```

```js
let string = 'I love JavaScript. If you do not love JavaScript what else can you love.'

console.log(string.lastIndexOf('love'))       // 67
console.log(string.lastIndexOf('you'))        // 63
console.log(string.lastIndexOf('JavaScript')) // 38
```

15. *concat()*: 它接受许多子字符串并将它们连接起来。

```js
string.concat(substring, substring, substring)
```

```js
let string = '30'
console.log(string.concat("Days", "Of", "JavaScript")) // 30DaysOfJavaScript

let country = 'Fin'
console.log(country.concat("land")) // Finland
```

16. *startsWith*: 它接受一个子字符串作为参数，并检查字符串是否以该指定的子字符串开头。它返回一个布尔值（true或false）。

```js
//语法
string.startsWith(substring)
```

```js
let string = 'Love is the best to in this world'

console.log(string.startsWith('Love'))   // true
console.log(string.startsWith('love'))   // false
console.log(string.startsWith('world'))  // false

let country = 'Finland'

console.log(country.startsWith('Fin'))   // true
console.log(country.startsWith('fin'))   // false
console.log(country.startsWith('land'))  //  false
```

17. *endsWith*: 它接受一个子字符串作为参数，并检查字符串是否以该指定的子字符串结尾。它返回一个布尔值（true或false）。

```js
string.endsWith(substring)
```

```js
let string = 'Love is the most powerful feeling in the world'

console.log(string.endsWith('world'))         // true
console.log(string.endsWith('love'))          // false
console.log(string.endsWith('in the world')) // true

let country = 'Finland'

console.log(country.endsWith('land'))         // true
console.log(country.endsWith('fin'))          // false
console.log(country.endsWith('Fin'))          //  false
```

18. *search*: 它接受一个子字符串作为参数，并返回第一个匹配的索引。搜索值可以是字符串或正则表达式模式。

```js
string.search(substring)
```

```js
let string = 'I love JavaScript. If you do not love JavaScript what else can you love.'
console.log(string.search('love'))          // 2
console.log(string.search(/javascript/gi))  // 7
```

19. *match*: 它接受一个子字符串或正则表达式模式作为参数，如果有匹配则返回一个数组，如果没有则返回null。让我们看看正则表达式模式是什么样的。它以/符号开始，以/符号结束。

```js
let string = 'love'
let patternOne = /love/     // 没有任何标志
let patternTwo = /love/gi   // g-表示在整个文本中搜索，i - 不区分大小写
```

Match语法

```js
// 语法
string.match(substring)
```

```js
let string = 'I love JavaScript. If you do not love JavaScript what else can you love.'
console.log(string.match('love'))
```

```sh
["love", index: 2, input: "I love JavaScript. If you do not love JavaScript what else can you love.", groups: undefined]
```

```js
let pattern = /love/gi
console.log(string.match(pattern))   // ["love", "love", "love"]
```

让我们使用正则表达式从文本中提取数字。这不是正则表达式部分，不要惊慌！我们稍后会介绍正则表达式。

```js
let txt = 'In 2019, I ran 30 Days of Python. Now, in 2020 I am super exited to start this challenge'
let regEx = /\d+/

// d与转义字符表示d不是普通的d，而是充当数字
// +表示一个或多个数字，
// 如果后面有g，则表示全局，搜索所有地方。

console.log(txt.match(regEx))  // ["2", "0", "1", "9", "3", "0", "2", "0", "2", "0"]
console.log(txt.match(/\d+/g)) // ["2019", "30", "2020"]
```

20. *repeat()*: 它接受一个数字作为参数，并返回字符串的重复版本。

```js
string.repeat(n)
```

```js
let string = 'love'
console.log(string.repeat(10)) // lovelovelovelovelovelovelovelovelovelove
```

## 检查数据类型和类型转换 {#checking-data-types-and-casting}

### 检查数据类型 {#checking-data-types}

要检查某个变量的数据类型，我们使用 *typeof* 方法。

**示例：**

```js
// 不同的JavaScript数据类型
// 让我们声明不同的数据类型

let firstName = 'Asabeneh'      // 字符串
let lastName = 'Yetayeh'        // 字符串
let country = 'Finland'         // 字符串
let city = 'Helsinki'           // 字符串
let age = 250                   // 数字，这不是我的真实年龄，不用担心
let job                         // undefined，因为没有赋值

console.log(typeof 'Asabeneh')  // string
console.log(typeof firstName)   // string
console.log(typeof 10)          // number
console.log(typeof 3.14)        // number
console.log(typeof true)        // boolean
console.log(typeof false)       // boolean
console.log(typeof NaN)         // number
console.log(typeof job)         // undefined
console.log(typeof undefined)   // undefined
console.log(typeof null)        // object
```

### 改变数据类型（类型转换）{#changing-data-type-casting}

- 类型转换：将一种数据类型转换为另一种数据类型。我们使用 _parseInt()_、_parseFloat()_、_Number()_、_+ 号_、_str()_
  当我们进行算术运算时，字符串数字应该首先转换为整数或浮点数，否则它会返回错误。

#### 字符串转整数 {#string-to-int}

我们可以将字符串数字转换为数字。引号内的任何数字都是字符串数字。字符串数字的示例：'10'、'5' 等。
我们可以使用以下方法将字符串转换为数字：

- parseInt()
- Number()
- 加号(+)

```js
let num = '10'
let numInt = parseInt(num)
console.log(numInt) // 10
```

```js
let num = '10'
let numInt = Number(num)

console.log(numInt) // 10
```

```js
let num = '10'
let numInt = +num

console.log(numInt) // 10
```

#### 字符串转浮点数 {#string-to-float}

我们可以将字符串浮点数转换为浮点数。引号内的任何浮点数都是字符串浮点数。字符串浮点数的示例：'9.81'、'3.14'、'1.44' 等。
我们可以使用以下方法将字符串浮点数转换为数字：

- parseFloat()
- Number()
- 加号(+)

```js
let num = '9.81'
let numFloat = parseFloat(num)

console.log(numFloat) // 9.81
```

```js
let num = '9.81'
let numFloat = Number(num)

console.log(numFloat) // 9.81
```

```js
let num = '9.81'
let numFloat = +num

console.log(numFloat) // 9.81
```

#### 浮点数转整数 {#float-to-int}

我们可以将浮点数转换为整数。
我们使用以下方法将浮点数转换为整数：

- parseInt()
  
```js
let num = 9.81
let numInt = parseInt(num)

console.log(numInt) // 9
```

🌕  你太棒了。你已经完成了第2天的挑战，你在通往伟大的道路上又前进了两步。现在为你的大脑和肌肉做一些练习吧。

## 💻 第2天：练习 {#-day-2-exercises}

### 练习：级别 1 {#exercise-level-1}

1. 声明一个名为 challenge 的变量，并将其初始值赋为 **'30 Days Of JavaScript'**。
2. 使用 __console.log()__ 在浏览器控制台中打印字符串
3. 使用 _console.log()_ 在浏览器控制台中打印字符串的 __长度__
4. 使用 __toUpperCase()__ 方法将所有字符串字符更改为大写字母
5. 使用 __toLowerCase()__ 方法将所有字符串字符更改为小写字母
6. 使用 __substr()__ 或 __substring()__ 方法剪切（切片）字符串的第一个单词
7. 从 *30 Days Of JavaScript* 中切片出短语 *Days Of JavaScript*。
8. 使用 __includes()__ 方法检查字符串是否包含单词 __Script__
9. 使用 __split()__ 方法将 __字符串__ 拆分为 __数组__
10. 使用 __split()__ 方法在空格处拆分字符串 30 Days Of JavaScript
11. 'Facebook, Google, Microsoft, Apple, IBM, Oracle, Amazon' 在逗号处 __拆分__ 字符串并将其更改为数组。
12. 使用 __replace()__ 方法将 30 Days Of JavaScript 更改为 30 Days Of Python。
13. '30 Days Of JavaScript' 字符串中索引 15 处的字符是什么？使用 __charAt()__ 方法。
14. 使用 __charCodeAt()__ 获取 '30 Days Of JavaScript' 字符串中 J 的字符代码
15. 使用 __indexOf__ 确定 30 Days Of JavaScript 中 __a__ 第一次出现的位置
16. 使用 __lastIndexOf__ 确定 30 Days Of JavaScript 中 __a__ 最后一次出现的位置。
17. 使用 __indexOf__ 在以下句子中找到单词 __because__ 第一次出现的位置：__'You cannot end a sentence with because because because is a conjunction'__
18. 使用 __lastIndexOf__ 在以下句子中找到单词 __because__ 最后一次出现的位置：__'You cannot end a sentence with because because because is a conjunction'__
19. 使用 __search__ 在以下句子中找到单词 __because__ 第一次出现的位置：__'You cannot end a sentence with because because because is a conjunction'__
20. 使用 __trim()__ 移除字符串开头和结尾的任何尾随空格。例如 ' 30 Days Of JavaScript '。
21. 对字符串 *30 Days Of JavaScript* 使用 __startsWith()__ 方法并使结果为 true
22. 对字符串 *30 Days Of JavaScript* 使用 __endsWith()__ 方法并使结果为 true
23. 使用 __match()__ 方法在 30 Days Of JavaScript 中找到所有的 __a__
24. 使用 __concat()__ 合并 '30 Days of' 和 'JavaScript' 为单个字符串 '30 Days Of JavaScript'
25. 使用 __repeat()__ 方法打印 30 Days Of JavaScript 2 次

### 练习：级别 2 {#exercise-level-2}

1. 使用 console.log() 打印以下语句：

    ```sh
    The quote 'There is no exercise better for the heart than reaching down and lifting people up.' by John Holmes teaches us to help one another.
    ```

2. 使用 console.log() 打印以下 Mother Teresa 的名言：

    ```sh
    "Love is not patronizing and charity isn't about pity, it is about love. Charity and love are the same -- with charity you give love, so don't just give money but reach out your hand instead."
    ```

3. 检查 typeof '10' 是否完全等于 10。如果不是，使其完全相等。
4. 检查 parseFloat('9.8') 是否等于 10，如果不是，使其与 10 完全相等。
5. 检查 'on' 是否同时存在于 python 和 jargon 中
6. _I hope this course is not full of jargon_。检查句子中是否有 _jargon_。
7. 生成一个介于 0 和 100 之间（包含）的随机数。
8. 生成一个介于 50 和 100 之间（包含）的随机数。
9. 生成一个介于 0 和 255 之间（包含）的随机数。
10. 使用随机数访问 'JavaScript' 字符串字符。
11. 使用 console.log() 和转义字符打印以下模式。

    ```js
    1 1 1 1 1
    2 1 2 4 8
    3 1 3 9 27
    4 1 4 16 64
    5 1 5 25 125
    ```

12.  使用 __substr__ 从以下句子中切片出短语 __because because because__：__'You cannot end a sentence with because because because is a conjunction'__

### 练习：级别 3 {#exercises-level-3}

1. 'Love is the best thing in this world. Some found their love and some are still looking for their love.' 计算这句话中 __love__ 这个词的数量。
2. 使用 __match()__ 计算以下句子中所有 __because__ 的数量：__'You cannot end a sentence with because because because is a conjunction'__
3. 清理以下文本并找到最频繁的词（提示，使用 replace 和正则表达式）。

    ```js
        const sentence = '%I $am@% a %tea@cher%, &and& I lo%#ve %te@a@ching%;. The@re $is no@th@ing; &as& mo@re rewarding as educa@ting &and& @emp%o@weri@ng peo@ple. ;I found tea@ching m%o@re interesting tha@n any ot#her %jo@bs. %Do@es thi%s mo@tiv#ate yo@u to be a tea@cher!? %Th#is 30#Days&OfJavaScript &is al@so $the $resu@lt of &love& of tea&ching'
    ```

4. 通过从以下文本中提取数字来计算此人的年总收入。'He earns 5000 euro from salary per month, 10000 euro annual bonus, 15000 euro online courses per month.'

🎉 恭喜！🎉

[<< 第1天](../readMe.md) | [第3天 >>](../03_Day_Booleans_operators_date/03_booleans_operators_date.md)