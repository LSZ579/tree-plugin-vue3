## 置顶
**<font color = red size=5>定制开发、技术支持/咨询可以加我微信：122720267</font>**
**<font color = red size=4>tips：收徒</font>**
## 版本介绍
该版本是vue3版本，vue2版本请前往：https://ext.dcloud.net.cn/plugin?id=2423

<font size='4'>一次性数据返回演示地址：[点击跳转](https://lsz579.github.io/xiaolu-tree-plugin/#/)</font>

<font size='4'>异步加载版：[点击跳转](https://lusz.top/picture/treeload/#/)</font>

<font size='4'>其它树形结构：[点击跳转](https://lusz.top/picture/h5/#/)</font>

#### 1.1功能介绍
##### 1、多选: 支持多选任意多项，支持关联子级，仅选中子级，全选，半选状态
##### 2、单选状态可以回显选中的位置路径
##### 3、只需传checkList字段就可以回显默认选中，清空选择只需要清空checklist字段
使用示例

```bash
<xiaolu-tree  :checkList="checkList"  v-if="tree.length>0"  :options="prop" @sendValue="confirm"  :isCheck="true" :treeNone="tree"></xiaolu-tree>
```

图1 多项选择，选择任意多项

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/2021051112360651.gif#pic_center)
 
图2 多项选择，关联子级，支持全选，和取消全选，半选状态

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210511123742433.gif#pic_center)

##### 2、单选
图1  可以选择任意一项或只能选择子项，选择后进入可以自动切换到选中页面的路径

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210511124022190.gif#pic_center)


#### 参数说明
|参数   | 类型  | 是否必填 |  默认值  |  说明 |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| treeNone   | Array   | 是  |  [ ] | 传入的树形结构数据，每个对象必须包含唯一的keyValue值  |
| keyValue| String   | 否  |  id | 唯一的key值,必须是唯一的才行（纯展示可不带）  |
|  searchIf | Boolean  |否   |true  |是否开启搜索框   |
| isCheck  | Boolean  |  否 |false  | 是否开启选择操作，值是false时仅展示，无操作  |
| options | Object  | 否  |{label:'name',children:'children'}   |  参数配置，详细见下表 |
| checkList | Array  | 是  |  []   |  默认选中值，根据id字段匹配   |
#### 方法
|方法名| 参数 |说明|
|--|--|--|
| sendValue | val | val 接收选中的数据，数据类型为数组| 
#####  options参数说明
|参数   | 类型  | 是否必填 |  默认值  |  说明 |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| label  | string  | 否  |  name | 指定选项标签为选项对象的某个属性值  |
|  children |  string | 否 | children  |指定选项的子选项为选项对象的某个属性值
|  multiple |  Boolean | 否 | true  |值为true时为多选，为false时是单选
|  checkStrictly|  Boolean | 否 | false| 需要在多选模式下才传该值，checkStrictly为false时，可让父子节点取消关联，选择任意一级选项。为true时关联子级，可以全选
|  nodes|  Boolean | 否 | true|在单选模式下，nodes为false时，可以选择任意一级选项，nodes为true时，只能选择叶子节点

#####  options参数示例

```bash
	options: {//多项模式(任意选中多项)
		label: 'name',
		children: 'children',
		multiple:true
	},
	options: {//多项模式(关联子级)
		label: 'name',
		children: 'children',
		multiple:true,
		checkStrictly:true
	},
	options: {//单选模式(任意一项)
		label: 'name',
		children: 'children',
		multiple:false,
		nodes:false
	},
	options: {//单选模式选user
		label: 'name',
		children: 'children',
		multiple:false,
		nodes:true
	}*
```
`

### 传入的数据结构说明：

1. id，user字段必须，user'字段名不可更改，id的字段明可以通过传keyValue指定，user为true时说明没有子级，user未false时说明有子级（即children的长度不为0）

```bash
[
	{
		id: 664214366998,
		name: "校长443",
		user: false,
		children: [{
			id: 885655454545454545678,
			name: "小陆",
			user: true
		}]
	},
]
```
### 选中返回的结果checkList：返回一个二维数组

```bash
[
	{
		id: xxx,
		name: "xxx",
		user: false,
		path:[],//该值的路径
	},
]
```
## 常见问题
#### 1.如何清空选中？

```bash
把checkList设为空即可
如checkList=[]
```
#### 2.数据无法显示/或组件无法运行

```bash
请到GitHub上拉取完整的示例代码运行一遍，再导入自己的项目中
```
[获取完整示例代码](https://github.com/LSZ579/xiaolu-tree-plugin)
#### 3. 多选关联子级没返回父级

```bash
多选并关联子级的模式下，只会返回user为true的用户，不返回含有子级的
可以通过返回的数据中的path路径获取父级
```

## 4.结语

**<font  size='5'>项目将持续维护更新，欢迎提建议<font>**

