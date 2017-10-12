## 1.map



有返回值，返回一个新的数组，每个元素为调用func的结果。



\`\`\`

let list = \[1, 2, 3, 4, 5\];

let other = list.map\(\(d, i\) =&gt; {

    return d \* 2;

}\);

console.log\(other\);

// print: \[2, 4, 6, 8, 10\]

\`\`\`



## 2.filter



有返回值，返回一个符合func条件的元素数组

\`\`\`

let list = \[1, 2, 3, 4, 5\];

let other = list.filter\(\(d, i\) =&gt; {

    return d % 2;

}\);

console.log\(other\);

// print: \[1, 3, 5\] 

\`\`\`

\#\#3.some



返回一个boolean，判断是否有元素符合func条件，如果有一个元素符合func条件，则循环会终止。

\`\`\`

let list = \[1, 2, 3, 4, 5\];

list.some\(\(d, i\) =&gt; {

    console.log\(d, i\);

    return d &gt; 3;

}\);

// print: 1,0 2,1 3,2 4,3

// return false

\`\`\`

## 4.every



返回一个boolean，判断每个元素是否符合func条件，有一个元素不满足func条件，则循环终止，返回false。

\`\`\`

let list = \[1, 2, 3, 4, 5\];

list.every\(\(d, i\) =&gt; {

    console.log\(d, i\);

    return d &lt; 3;

}\);

// print: 1,0 2,1 3,2

// return false

\`\`\`

## 5.forEach



没有返回值，只针对每个元素调用func。

优点：代码简介。

缺点：无法使用break，return等终止循环。

\`\`\`

let list = \[1, 2, 3, 4, 5\];

let other = \[\];

list.forEach\(\(d, i\) =&gt; {

    other.push\(d \* 2\);

}\);

console.log\(other\);

// print: \[2, 4, 6, 8, 10\]

\`\`\`

## 6.for in



for-in循环实际是为循环”enumerable“对象而设计的，for in也可以循环数组，但是不推荐这样使用，for–in是用来循环带有字符串key的对象的方法。

缺点：只能获得对象的键名，不能直接获取键值。

\`\`\`

var obj = {a:1, b:2, c:3};

for \(var prop in obj\) {

  console.log\("obj." + prop + " = " + obj\[prop\]\);

}

// print:  "obj.a = 1" "obj.b = 2" "obj.c = 3"

\`\`\`

## 7.for of



for of为ES6提供，具有iterator接口，就可以用for of循环遍历它的成员。也就是说，for of循环内部调用的是数据结构的Symbol.iterator方法。

for of循环可以使用的范围包括数组、Set和Map结构、某些类似数组的对象（比如arguments对象、DOM NodeList对象）、后文的Generator对象，以及字符串。

有些数据结构是在现有数据结构的基础上，计算生成的。比如，ES6的数组、Set、Map都部署了以下三个方法，调用后都返回遍历器对象。

### entries



entries\(\) 返回一个遍历器对象，用来遍历\[键名, 键值\]组成的数组。对于数组，键名就是索引值；对于Set，键名与键值相同。Map结构的iterator接口，默认就是调用entries方法。



### keys



keys\(\) 返回一个遍历器对象，用来遍历所有的键名。



### values



values\(\) 返回一个遍历器对象，用来遍历所有的键值。 

这三个方法调用后生成的遍历器对象，所遍历的都是计算生成的数据结构。

\`\`\`

// 字符串

let str = "hello";

for \(let s of str\) {

  console.log\(s\); // h e l l o

}



// 遍历数组

let list = \[1, 2, 3, 4, 5\];

for \(let e of list\) {

    console.log\(e\);

}

// print: 1 2 3 4 5



// 遍历对象

obj = {a:1, b:2, c:3};

for \(let key of Object.keys\(obj\)\) {

  console.log\(key, obj\[key\]\);

}

// print:  a 1 b 2 c 3

说明：对于普通的对象，for...in循环可以遍历键名，for...of循环会报错。

一种解决方法是，使用Object.keys方法将对象的键名生成一个数组，然后遍历这个数组。



// entries

let arr = \['a', 'b', 'c'\];

for \(let pair of arr.entries\(\)\) {

  console.log\(pair\);

}

// \[0, 'a'\]

// \[1, 'b'\]

// \[2, 'c'\]

\`\`\`

