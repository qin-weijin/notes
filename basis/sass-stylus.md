## SASS 函数

**String**

| Func | Description |
| ---- | ----------- |
| `quote(string)` | 添加引号 |
| `str-index(string,substring)` | return substring 在 string 的 index |
| `str-insert(string,insert,index)` | 插入 inset 到 string 从 index 开始 |
| `str-length(string)` | return 长度 |
| `str-slice(string,start,end)` | 截取字符串 |
| `to-lower-case(string)` | 小写 |
| `to-upper-case(string)` | 大写 |
| `unique-id()` | return 随机字符串 用于 id |
| `unquote(string)` | 移除 引号 |

**Number**

| Func | Description |
| ---- | ----------- |
| `abs(num)` | 绝对值 |
| `ceil(num)` | 向上取整 |
| `comparaable(num1,num2)` | 是否能比较的单位 true|false |
| `floor(num)` | 向下取整 |
| `max(num...)` | return 最大 num |
| `min(num...)` | return 最小 num |
| `percentage(num)` | 转换 百分比 |
| `random(num*)` | 指定num:return 1-num 随机整数。 无指定num:return 0-1 |
| `round(num)` | 四舍五入 |

**List**

| Func | Description |
| ---- | ----------- |
| `append(list,value,separator)` | 添加 value 到 list  |
| `index(list,value)` | return value 的 index |
| `is-bracketed(list)` | 判断 list 是否带中括号 |
| `join(list1,list2,separator)` | 合并 list2 到 list1，separator 分隔符  |
| `length(list)` | return list.length |
| `list-separator(list)` | return 分隔符类型 "space" "comma" |
| `nth(list,n)` | return list[n] |
| `set-nth(list,n,value)` | set list[n] 为 value |
| `zip(lists)` | 合并 多个list为一个多维list

**Map**

| Func | Description |
| ---- | ----------- |
| `map-get(map,key)` | return 变量 map 中对应的key的value |
| `map-has-key(map,key)` | 检测 是否有 key |
| `map-keys(map)` | return 所有 key |
| `map-merge(map1,map2)` | 将 map2 添加到 map1 |
| `map-remove(map,keys...)` | 移除指定 key |
| `map-values(map)` | return 所有 value

**Selector**

| Func | Description |
| ---- | ----------- |
| `is-superselector(sele1,sele1)` | return sele1 是否包含 sele2 |
| `selector-append(sele1,seles)` | 连接多个选择器  |
| `selector-extend(selector,extendee,extender)` |
| `selector-nest(seles)` | return 嵌套的选择器 |
| `selector-parse(selector)` | 将字符串转换为选择器 |
| `selector-replace(sele,o,re)` | 更换 sele o 为 re |
| `selector-unify(sele1,sele2)` | 合并选择器 |
| `simple-selectors(sele)` | 拆分选择器

**Introspection**

| Func | Description |
| ---- | ----------- |
| `call(function,arguments...)` | 动态调用函数 |
| `content-exists()` | 当前混入是否传递 @content |
| `feature-exists(feature)` | 检测 是否支持 feature |
| `function-exists(func)` | 检测 函数是否存在 |
| `get-function(func,css:true|false)` |   |
| `global-variable-exists(vari)` | 检测 变量是否定义 |
| `inspect(value)` | 以字符串形式返回 value |
| `mixin-exists(mixin)` | 检测 混入是否存在 |
| `type-of(value)` | return value 类型 |
| `unit(value)` | return value 单位 |
| `unitless(value)` | 检测 value是否带单位 |
| `variable-exists(vari)` | 检测 vari 是否在当前作用域

**Color**

| Func | Description |
| ---- | ----------- |
| `rgb(r,g,b)` | 创建(RGB) |
| `rgba(r,g,b,a)` | 创建(RGBA) |
| `hsl(h,s,l)` | 创建(HSL) |
| `hsla(h,s,l,a)` | 创建(HSLA) |
| `grayscale(color)` | return 灰度  |
| `complement(color)` | return 补色 180deg |
| `invert(color,weight)` | return 反色 |
| `rgba(color,alpha)` | 创建 指定透明度的color |
| `lighten(color,amount)` | 创建 提高亮度的color |
| `darken(color,amount)` | 创建 降低亮度的color |
| `saturate(color,amount)` | 创建 提高透明度的color |
| `desaturate(color,amount)` | 创建 降低饱和度的color |
| `opacify(color,amount)` | 创建 降低透明度的color |
| `fade-in(color,amount)` | 创建 降低透明度的color |
| `transparentize(color,amount)` | 创建 提高透明度的color |
| `fade-out(color,amount)` | 创建 提升透明度的color |
| `red(color)` | return r 值 |
| `green(color)` | return g 值 |
| `blue(color)` | return b 值 |
| `hue(color)` | return h 值 |
| `saturation(color)` | return s 值 |
| `lightness(color)` | return l 值 |
| `alpha(color)` | return a 值 |
| `opacity(color)` | return 透明度 |
| `mix(color1,color2,weight)` | 混色相加 weight表示color1占比 |
| `adjust-hue(color,degrees)` | 改变色相 degrees(-360deg - 360deg) |
| `adjust-color(color,r,g,b,h,s,l,a)` | 相加运算 color 相加给定值 |
| `change-colir(color,r,g,b,h,s,l,a)` | 替换运算 color 替换给定值 |
| `scale-color(color,r,g,b,h,s,l,a)` | 百分比加减运算 |

## Stylus Operator 运算符

| operator | Description |
| -------- | ----------- |
| `~` |  |
| `not true` | 逻辑非(优先级低于符号) |
| `!1` |  |
| `-1` |  |
| `+1` |  |
| `1 + 1s` | 强制单位转换 2s |
| `1 - 1` |  |
| `/` |  |
| `*`  |  |
| `%` | 取余 |
| `2 ** 2` | 指数 |
| `&&` | 别名 and |
| `||` | 别名 or |
| `|` | 比较:单位 颜色 字符串 标识符 |
| `==` | 别名 is |
| `!=` | 别名 is not 和 isnt |
| `>=` |  |
| `<=` | |
| `>` | |
| `<` | |
| `#fff is a rgba` | 别名 type() 类型检测 |
| `foo is defined` | 检测 foo 是否定义 |
| `1 in exp` | 检测 表达式|变量|标识符|元组 是否包含 值 |
| `1..5 => 1 2 3 4 5` |
| `1...5 => 1 2 3 4` |
| `args...` | 接受其余参数 |
| `表达式_1 ? 表达式_2 : 表达式_3` | |
| `color ?: white` | `if(color == defined){white}else{color}` |
| `color ?= white` |
| `color := white` |
| `\` | 字符转码 |

## Stylus 函数

| Stylus Func | Description |
| ----------- | ----------- |
| `p(expr)` | 检查返回值 |
| `unquote()` | 无法处理的属性值 |
| `push(expr,args…)` | 连接 expr |
| `unshift(expr, args…)` | 连接 expr 在前面 |
| `join(delim, args…)` | 连接 使用delim符号 |
| `red(color)` | red值 num |
| `green(color)` | green值 num |
| `blue(color)` | blue值 num |
| `alpha(color)` | alpha值 num |
| `dark(color)` | true|false 暗色 |
| `light(color)` | true|false 亮色 |
| `hue(color)` | 色调 deg |
| `saturation(color)` | 饱和度 百分比 |
| `lightness(color)` | 亮度 百分比 |
| `hsla(color | h,s,l,a)` | 转换 HSLA 表示法 |
| `hsl(color | h,s,l)` | 转换 HSL 表示法 |
| `rgba(color | r,g,b,a)` | 转换 RGBA 表示法 |
| `rgb(color | r,g,b)` | 转换 RGB 表示法 |
| `lighten(color, amount)` | 亮度 增 |
| `darken(color, amount)` | 亮度 减 |
| `saturate(color, amount)` | 饱和度 增 |
| `desaturate(color, amount)` | 饱和度 减 |
| `invert(color)` | 颜色反转 红绿蓝 |
| `unquote(str | ident)` | 去除引号 |
| `abs(unit)` | 绝对值 |
| `ceil(unit)` | 向上取整 |
| `floor(unit)` | 向下取整 |
| `round(unit)` | 四舍五入 |
| `min(a,b)` | 取较小 |
| `max(a,b)` | 取较大 |
| `even(unit)` | 检测 偶数 true|false |
| `odd(unit)` | 检测 奇数 true|false |
| `sum(nums)` | 求和 |
| `avg(nums)` | 平均数 |
| `keys($variable)` | 返回键 |
| `values($variable)` | 返回值 |
| `typeof(node)` | 返回类型 别名 type-of() type() |
| `unit(expr,type)` | return 强制type的字符串 |
| `match(pattern, string)` | 检测 string 匹配 pattern true|false |
| `operate(op,arg1,arg1)` | 执行 op 二元运算 |
| `length(arguments)` | 参数长度 |
| `warn(msg)` | msg 警告 |
| `error(msg)` | 错误并退出 |
| `last(expr)` | return expr 最后的值 |
| `opposite-position(positions)` | 相反值 |
| `image-size(path)` | path路径图片的 width & height |
| `add-property(name, expr)` | 给最近的块添加属性 name:expr |