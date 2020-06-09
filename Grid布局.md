### Grid布局

[TOC]



### 容器属性

#### 1.grid-template-columns /grid-template-rows     定义每一列的列宽 /行宽 

```css
1.使用绝对单位，也可以使用百分比
   grid-template-columns: 100px 100px 100px;
   grid-template-rows: 33.3% 33.3%  33.3%;
2.repeat(次数，重复的值) 
   grid-template-columns: repeat(3,100px);
   grid-template-rows: repeat(3,33.3%);
   grid-template-rows: repeat(3,100px 20px 30px ...); 重复某种模式也是可以的。
   grid-template-columns: repeat(auto-fill, 100px); auto-fill 关键字 自动填充，直到容器不能放置更多的列。
   grid-template-columns: repeat(3, 1fr); fr 关键字  表示比例关系， 可以与绝对长度的单位结合使用，
   grid-template-columns: 1fr 100px 2fr;  
   grid-template-columns: 1fr 1fr 2fr;
3. minmax()函数产生一个长度范围，表示长度就在这个范围之中。它接受两个参数，分别为最小值和最大值。
   grid-template-columns: 1fr 1fr minmax(100px, 1fr);
4.auto 关键字  表示由浏览器自己决定长度。
   grid-template-columns: 100px auto 100px;
5.可以使用方括号，指定每一根网格线的名字.允许同一根线有多个名字，比如[fifth-line row-5]。
   grid-template-columns: [c1] 100px [c2] 100px [c3] auto [c4];
   grid-template-rows: [r1] 100px [r2] 100px [r3] auto [r4];
   
```

#### 2.row-gap 属性， 设置行与行的间隔（行间距）  column-gap 属性，  设置列与列的间隔（列间距）。 

#### gap 属性  行和列的简写属性

```css
  row-gap: 20px;
  column-gap: 20px;
  gap: <row-gap> <column-gap>;
  gap: 20px 20px;
```

#### 3.grid-template-areas    用于定义区域。

 区域的命名会影响到网格线。每个区域的起始网格线，会自动命名为区域名-start，终止网格线自动命名为区域名-end。`比如，区域名为header，则起始位置的水平网格线和垂直网格线叫做header-start，终止位置的水平网格线和垂直网格线叫做header-end。`

```css
grid-template-columns: 100px 100px 100px;
  grid-template-rows: 100px 100px 100px;
  grid-template-areas: 'a b c'
                       'd e f'
                       'g h i';
多个单元格合并成一个区域
grid-template-areas: 'a a a'
                     'b b b'
                     'c c c';
某些区域不需要利用，则使用"点"（.）表示。

grid-template-areas: 'a . c'
                     'd . f'
                     'g . i';
```

#### 4.grid-auto-flow 属性    放置 顺序 

 ` 默认的放置顺序是"先行后列"，即先填满第一行，再开始放入第二行 `

```css
      grid-auto-flow: column; // row column，row dense  column dense。
      row dense  表示"先行后列"，并且尽可能紧密填满，尽量不出现空格。
```

#### 5.justify-items 属性， align-items 属性，   设置单元格内容的水平/垂直位置。 

####  place-items 属性  合并属性

```css
  justify-items: start | end | center | stretch;
  align-items: start | end | center | stretch;
     start：对齐单元格的起始边缘。
     end：对齐单元格的结束边缘。
     center：单元格内部居中。
     stretch：拉伸，占满单元格的整个宽度（默认值）。
place-items: <align-items> <justify-items>;
    place-items: start end;
```

#### 6.justify-content 属性 align-content 属性， 整个内容区域在容器里面的水平/垂直位置

####  place-content 属性     合并属性

```css
   justify-content: start | end | center | stretch | space-around | space-between | space-evenly;
   align-content: start | end | center | stretch | space-around | space-between | space-evenly;  
          start - 对齐容器的起始边框。
          end - 对齐          容器的结束边框。
          center - 容器内部居中。
          stretch - 项目大小没有指定时，拉伸占据整个网格容器。
          space-around - 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与容器边框的间隔大一倍。
          space-between - 项目与项目的间隔相等，项目与容器边框之间没有间隔。
          space-evenly - 项目与项目的间隔相等，项目与容器边框之间也是同样长度的间隔。
place-content: <align-content> <justify-content>
   place-content: space-around space-evenly;
```

#### 7.grid-auto-columns 属性， grid-auto-rows 属性

  项目的指定位置，在现有网格的外部  浏览器会自动生成多余的网格，以便放置项目。    不指定这两个属性，浏览器完全根据单元格内容的大小，决定新增网格的列宽和行高。 

```css
grid-auto-rows: 50px; 
```

#### 8.grid-template 属性， grid 属性

grid-template 属性，  `grid-template-columns`、`grid-template-rows`和`grid-template-areas`这三个属性的合并简写形式。

 grid 属性  是`grid-template-rows`、`grid-template-columns`、`grid-template-areas`、 `grid-auto-rows`、`grid-auto-columns`、`grid-auto-flow`这六个属性的合并简写形式。 

## 项目属性

#### 1.grid-column-start 属性， grid-column-end 属性， grid-row-start 属性， grid-row-end 属性 

-  指定项目的四个边框，分别定位在哪根网格线   

#### grid-column 属性， grid-row 属性 合并属性

```css
1.指定为第几个网格线
  grid-column-start: 2;
  grid-column-end: 4;左边框是第二根垂直网格线，右边框是第四根垂直网格线。
2.可以指定为网格线的名字。
   grid-column-start: header-start;
   grid-column-end: header-end;
3.可以使用span关键字，表示"跨越"，即左右边框（上下边框）之间跨越多少个网格。
   grid-column-start: span 2;
//合并属性
1.指定为第几个网格线
  grid-column: 1 / 3;
  grid-row: 1 / 2;
2.使用span关键字，表示跨越多少个网格。
  grid-column: 1 / span 2;
  grid-row: 1 / span 2;
```

#### 2.grid-area 属性      指定项目放在哪一个区域。 

-  可用作`grid-row-start`、`grid-column-start`、`grid-row-end`、`grid-column-end`的合并简写形式 

```css
     grid-area: e;
 grid-area: <row-start> / <column-start> / <row-end> / <column-end>;
     grid-area: 1 / 1 / 3 / 3;
```

#### 3.justify-self 属性， align-self 属性， 设置单元格内容的水平/垂直位置

 place-self 属性  合并属性

```css
 justify-self: start | end | center | stretch;
  align-self: start | end | center | stretch;
          start：对齐单元格的起始边缘。
          end：对齐单元格的结束边缘。
          center：单元格内部居中。
          stretch：拉伸，占满单元格的整个宽度（默认值）。   
place-self: <align-self> <justify-self>;
    place-self: center center; 如果省略第二个值，place-self属性会认为这两个值相等。
```