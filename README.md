# 说明文档
## `math-computer`: 一个帮助你解决JS计算精度的问题

如何安装？

```shell
npm install @malp/math-computer
or
yarn add @malp/math-computer
```

## 引入项目

```javascript
import { add, sub } from '@malp/math-computer'

//使用
const sum = add(0.1, 0.2)
```

如果不想开启数组越界检查（默认开启）：

```javascript
import MathComputer from '@malp/math-computer'
const mathComputer = new MathComputer(false)

//使用
const sum = mathComputer.add(0.1, 0.2)
```

## 方法文档

目前提供十个功能：

	1. strip：处理JS小数精度方法
	1. digitLength：返回小数的位数（支持科学计数法）
	1. add：精确加法(支持科学计数法)
	1. sub：精确减法(支持科学计数法)
	1. mul：精确乘法(支持科学计数法)
	1. div：精确除法(支持科学计数法)
	1. surp：精确取余(支持科学计数法)
	1. float2Fixed：将小数转换为整数(支持科学计数法)
	1. checkBoundary：检查数字是否越界(支持科学计数法)
	1. round：四舍五入(支持科学计数法)

### 方法案例

	1. strip
    + strip(0.09999999999999998) = 0.1
	2. digitLength
    + digitLength(0.02) = 2
    + digitLength(2e-4) = 4
	3. add(不定参数)
    + add(0.1, 0.2) = 0.3
    + add(0.1, 0.2, 0.3) = 0.7
    + add(1e-1, 2e-1) = 0.3
	4. sub(不定参数)
    + sub(0.3, 0.1) = 0.2
    + sub(0.5, 0.2, 0.1) = 0.2
    + sub(3e-1, 1e-1) = 0.2
	5. mul(不定参数)
    + mul(0.2, 0.1) = 0.02
    + mul(0.2, 0.1, 0.1) = 0.002
    + mul(2e-1, 1e-1) = 0.02
	6. div(不定参数)
    + div(0.04, 0.2) = 0.2
    + div(0.04, 0.2, 0.1) = 2
    + div(4e-2, 2e-1) = 0.2
	7. surp(不定参数)
    + surp(1.1, 1) = 0.1
    + surp(2.1, 1, 0.03) = 0.01
    + surp(11e-1, 1) = 0.1
	8. float2Fixed
    + float2Fixed(2.4) = 24
    + float2Fixed(2.4e-4) = 24
	9. checkBoundary
    + checkBoundary(Number.MAX_SAFE_INTEGER + 1)
	10. round
     + round(1.5555, 2) = 1.56
     + round(1.5555, 1) = 1.6
     + round(15555e-4, 2) = 1.56