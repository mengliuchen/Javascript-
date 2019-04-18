# Javascript-
1. ["1","2","3"].map(parseInt)
Array.map(function(value,index,arry1){}) 可使用最多三个参数来声明回调函数，第一个是数组的值，第二个是参数，array1是包含该元素的数组对象。parseInt(string,radix)前一个参数是字符串，后一个参数是要解析的数字的基数，该值介于2~36之间。小于2或者大于36，返回NaN
2. [typeof null, null instanceof Object]
typeof是一个获取变量或者表达式的类型的操作符（不是函数），null是特殊的object类型的值，所以typeof是Object，这里注意typeof返回的是字符串，instanceof表示某个变量是否是某个对象的实例，返回false
3. [[3,2,1].reduce(Math.pow),[].reduce(Math.pow)]
reduce方法接收一个函数作为累加器，数组中的每个值从左到右开始缩减，最终计算为一个值。 reduce() 对于空数组是不会执行回调函数的，所以报错。[3,2,1].reduce(Math.pow)最终结果为9。
4. var val = 'value';console.info('Value id '+(val === 'value')?'Something':'Nothing');
字符串拼接的优先级最高，所以'Value id '+(val === 'value')这一部分的结果是Value id true转化为布尔值是true所以输出为something
5. 
```var name = 'World';
(function(){
　　if(typeof name === 'undefined'){
　　　　var name = "Jack";
　　　　console.info('Goodbye '+ name);
　　}else{
　　　　console.info('Hello ' + name);
　　}
})();
```
理论上根据JS的作用域链，在函数中找不到变量，回去上一级找，但是在这个例子中if语句中对name进行了声明，这个
声明被提升，外部赋值被忽略，最终输出Goodbye Jack
6. 
```var START = END -100;
var count = 0;
for(var i = START ; i <= END ;i++){
　　count ++;
}
console.info(count);
```
END没有被声明，不知道这一个题问题所在
7. 
```
var arr = [0,1,2];
arr[10] = 10;
arr.filter(function(x){return x === undefined});
```
fiter会返回没有被赋值的元素，就是空数组
8. 
```
var two = 0.2;
var one = 0.1;
var eight = 0.8;
var six = 0.6;
[two -one == one,eight- six == two];
```
两个浮点数相加或者相减会导致一定的正常数据转换造成的精度丢失问题,结果是[true,false]。
9. 
```
function showCase(value){

　　switch(value){
　　　　case 'A':
　　　　　　console.info('Case A');
　　　　　　break;
　　　　case 'B':
　　　　　　console.info('Case B');
　　　　　　break;
　　　　case undefined :
　　　　　　console.info('undefined');
　　　　　　break;
　　　　default:
　　　　　　console.info('Do not know!');
　　}
}
showCase(new String('A'));
```
String的声明方式有三种，但产生的类型不尽相同，new 是产生一个空指针然后将对象作为this变量的值,返回的是一个String对象 {0:"A"}
10. 
```
function showCase(value){

　　switch(value){
　　　　case 'A':
　　　　　　console.info('Case A');
　　　　　　break;
　　　　case 'B':
　　　　　　console.info('Case B');
　　　　　　break;
　　　　case undefined :
　　　　　　console.info('undefined');
　　　　　　break;
　　　　default:
　　　　　　console.info('Do not know!');
　　}
}
showCase(String('A'));
```
使用String声明与直接声明效果一致。
11. 
```
function isOdd(num){
　　return num % 2 == 1; 
}
function isEven(num){
　　return num % 2 == 0; 
}
function isSane(num){
　　return isEven(num)||isOdd(num);
}
var values = [7,4,'13',-9,Infinity];
values.map(isSane);
```
"13"会被强制转换为13，-9余数会是-1，infinity结果是NaN
12. [parseInt(3,8),parseInt(3,2),parseInt(3,0)]
后面这个参数是指，以什么进制处理这个数，0就是10进制，以二进制无法处理3所以返回NaN，其余都是3
13.Array.isArray(Array.prototype) 
Array.prototype为[],Array.isArray(a)是一个判断a是否为数组的方法。所以返回true
14. 
```
var a = [0];
if([0]){
　　console.info(a == true);
}else{
　　console.info("else");
}
```
返回false，if比"=="宽松
15.  []==[]运行结果
数组在Javascript中是对象，每次使用[]都是新建一个新的对象，所以[]==[]不等
16.  [('5'+3),('5'-3)]
+具有拼接作用，-只是运算符
17. 1+-+++-+1
相当于1+(-(+(+(+(-(+1))))))，等于2
18. 
```
var arr = Array(3);
arr[0] = 2
arr.map(function(elem){return '1';});
```
虽然长度是3，但是只有一个赋值了，所以后面的不考虑，结果就是["1"]
19. 
```
function sidEffecting(arr){
　　arr[0] = arr[2];
}
function bar(a,b,c){
　　c = 10;
　　sidEffecting(arguments);
　　return a+b+c;
}
bar(1,1,1);
```
21

20. 
```
var a = 111111111111111110000;
b = 1111;
console.info(a+b);
```
数太大会失真，结果是111111111111111110000
21. 
```
var x = [].reverse;
x();
```
报错了,cannot convert undefined or null to object, 正确调用方式为x.call([])
22.  Number.MIN_VALUE>0
Number.MIN_VALUE表示的最小值为5e-324，MIN_VALUE代表的并不是负最小，而是最接近0的一个数，因此Number.MIN_VALUE>0。
23. [1<2<3,3<2<1]
true<3, true会被转换为1,1<3，最终返回true
false<1, false会被转换为0,0<1，返回true
24.  2 == [[[2]]]
a==b会把b转化为a的格式，[[[2]]]转化为2，结果是true
25.  [3.toString(),3..toString(),3...toString()]
[error,"3",error]， 3是数据型变量，不是Number实例，不能直接调用Number方法。3..toSting()会强制把3转化为数字实例
26. 
```
(function(){
　　var x1 =y1 =1;
})();

console.info(y1);
console.info(x1);
```
创建局部变量x1和全局变量y1，无法调用x1
27. 
```
function initButtons(){
　　var body = document.body,button,i;

　　for(i =0;i<5;i++){
　　　　button = document.createElement("button");
　　　　button.innerHTML = "Button" + i;
　　　　button.addEventListener("click",function(e){
　　　　　　alert(i);
　　　　},false);
　　　　body.appendChild(button);
　　}

}
initButtons();
```
虽然在页面上会显示值为button+i的按钮，但是点击任意一个按钮，最终都会显示5。
需要改为
```
function initButtons(){
        var body = document.body,button,i;

        for(i =0;i<5;i++){
            (function(i){
                button = document.createElement("button");
                button.innerHTML = "Button" + i;
                button.addEventListener("click",function(e){
                    alert(i);
                },false);
                body.appendChild(button);
            })(i);
            
        }

    }
    initButtons();
```
