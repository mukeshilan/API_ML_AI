# product requirements
发布日期 | 2018年11月25日
---|---
主题 | 动物识别
文件现状 | 进行中
作者 | 陈丽媛
设计师 | 无
开发者 | 无
测试者 | 无

# 目标
- 根据动物的实拍照片帮助用户识别动物，解释动物的品种、形态特等信息。

# 背景和战略契合处
- 用户在遇到陌生的动物会想要了解它的名字、种类等信息，这时候需要一个能识别的工具来帮助用户。

# 假定
- 所识别的动物外表未经过人为改变。
- 拍摄的照片不是虚构的。
- 用户使用时摄像机能够正常使用。
- 用户拍摄的照片足够清晰。

# 需求
标题 | 用户案例 | 重要程度 | 笔记
-----|----------|----------|-----
辨别动物品种 | 小明某天看到一只宠物狗，但是分不清它的品种是金毛还是拉布拉多 | 重要 | 动物识别
科普 | 大明带着小明外出游玩，看到一只昆虫，小明问大明昆虫这是什么动物 | 重要 | 儿童科普

# 使用者交互及设计
- 架构

![image](https://note.youdao.com/yws/api/personal/file/C450FAD3DDF244F696169C3EDC75BE5C?method=download&shareKey=52527f7e715be22a7c3dee26e19cc408)
# 问题
问题 | 结果
---|---
如何指导用户拍出更能识别的动物图片|给用户展示拍照图例提示用户
不能确认图片上的动物|列出可能是此动物的信息，提示用户换角度再次拍摄进行识别
识别特征不明显的动物（如：杂交犬类）| 显示大的类（例如：科：犬科）

# 将做
- 通过录制动物的声音来确定动物的类型。

# 加值宣言
- 百度云细粒度图像搜索-动物识别API在概率性识别动物种类，取得概率最大的结果与阿里云图像识别-动物识别API确定的动物种类对比，两者一致则确定此动物种类。确定种类后与百科知识图谱CN-DBpedia连接，取得此种类的信息。

# 核心价值
- 使用图像搜索API识别动物图片内容，提供相符的图片信息。使用API连接知识库，获得更全面的信息。

# 核心价值与用户痛点
- 喜欢动物的人或者户外爱好者看到不知名的动物会产生好奇心，但是又不知道这种动物叫什么，也没有什么工具能够证明。
- 家长教育孩子时偶尔会遇到不知名的动物，无法给孩子进行教育。

# 人工智能概率性与用户痛点
- 动物识别正确率在90%以上，适合非专业人群日常生活使用。

# 需求列表与人工智能API加值
- 图像分类
    - 百度云细粒度图像搜索-动物识别API：缩小范围，确定概率
    - 阿里云图像识别-动物识别API：识别准确率高达90%以上
- 知识图谱
    - 百科知识图谱CN-DBpedia：CN-DBpedia是由复旦大学知识工场实验室研发并维护的大规模通用领域结构化百科，其前身是复旦GDM中文知识图谱，是国内最早推出的也是目前最大规模的开放百科中文知识图谱，涵盖数千万实体和数亿级的关系，相关知识服务API累计调用量已达6亿次。
# 产品使用关键AI或机器学习之API的输出入展示
- 百度云细粒度图像搜索-动物识别API[（API文档）](http://ai.baidu.com/docs#/ImageClassify-API/562659ee)
    - 输入：一张图片（可正常解码，且长宽比较合适）
    - 输出：log_id；result；动物名称；可信度；对应识别结果的百科词条名称；对应识别结果百度百科页面链接；对应识别结果百科图片链接；对应识别结果百科内容描述
```
# encoding:utf-8
import base64
import urllib
import urllib2

'''
动物识别
'''

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v1/animal"

# 二进制方式打开图片文件
f = open('[本地文件]', 'rb')
img = base64.b64encode(f.read())

params = {"image":img,"top_num":6}
params = urllib.urlencode(params)

access_token = '[调用鉴权接口获取的token]'
request_url = request_url + "?access_token=" + access_token
request = urllib2.Request(url=request_url, data=params)
request.add_header('Content-Type', 'application/x-www-form-urlencoded')
response = urllib2.urlopen(request)
content = response.read()
if content:
    print content

```


```
HTTP/1.1 200 OK
x-bce-request-id: 73c4e74c-3101-4a00-bf44-fe246959c05e
Cache-Control: no-cache
Server: BWS
Date: Tue, 18 Oct 2016 02:21:01 GMT
Content-Type: application/json;charset=UTF-8
{
	"log_id": 7392482912853822863,
	"result": [{
		"score": "0.993811",
		"name": "叉角羚",
		"baike_info": {
			"baike_url": "http://baike.baidu.com/item/%E5%8F%89%E8%A7%92%E7%BE%9A/801703",
			"description": "叉角羚(学名：Antilocapra americana)：在角的中部角鞘有向前伸的分枝，故名。体型中等，体长1-1.5米，尾长7.5-10厘米，肩高81-104厘米，成体重36-60千克，雌体比雄体小；背面为红褐色，颈部有黑色鬃毛，腹部和臀部为白色，颊面部和颈部两侧有黑色块斑；毛被下面为绒毛，上覆以粗糙、质脆的长毛，由于某些皮肤肌的作用，能使其毛被呈不同角度，以利于保暖或散热。植食。叉角羚奔跑速度非常快，最高时速达100千米。一次跳跃可达3.5-6米。善游泳。夏季组成小群活动，冬季则集结成上百只的大群。为寻找食物和水源，一年中常进行几次迁移。性机警，视觉敏锐，能看到数千米外的物体。遇险时，臀部的白色毛能立起，向同伴告警。分布于北美洲。"
		}
	},
	{
		"score": "0.000289439",
		"name": "印度羚"
	},
	{
		"score": "0.000186248",
		"name": "藏羚羊"
	},
	{
		"score": "0.000147176",
		"name": "跳羚"
	},
	{
		"score": "0.000134434",
		"name": "驯鹿"
	},
	{
		"score": "9.86555e-05",
		"name": "高鼻羚羊"
	}]
}

```
- 阿里云图像识别-动物识别API[（API文档）](https://market.aliyun.com/products/57124001/cmapi028672.html?spm=5176.730005-56956004-57124001.productlist.d_cmapi028672.30b53524BbreOu&innerSource=search#sku=yuncode2267200001)
    - 输入：图片
    - 输出：物种类型

```
import urllib, urllib2, sys
import ssl


host = 'https://ocranimals.market.alicloudapi.com'
path = '/animal'
method = 'POST'
appcode = '你自己的AppCode'
querys = ''
bodys = {}
url = host + path

bodys['image'] = '''http://img3.fegine.com/image/sheep.png'''
//或者base64
//bodys['image'] = '''data:image/jpeg;base64,/9j/4A......'''
post_data = urllib.urlencode(bodys)
request = urllib2.Request(url, post_data)
request.add_header('Authorization', 'APPCODE ' + appcode)
//根据API的要求，定义相对应的Content-Type
request.add_header('Content-Type', 'application/x-www-form-urlencoded; charset=UTF-8')
ctx = ssl.create_default_context()
ctx.check_hostname = False
ctx.verify_mode = ssl.CERT_NONE
response = urllib2.urlopen(request, context=ctx)
content = response.read()
if (content):
    print(content)
```

```
{
  "code": "1",
  "msg": "查询成功",
  "animalType": "叉角羚"
}

```
- 百科知识图谱CN-DBpedia
    - 输入：实体名
    - 输出：实体全部的三元组知识
```
API / cndbpedia / avpair
输入实体名，返回实体全部的三元组知识

请求参数
q：实体名称（entity name）;必填项

apikey：开发者的访问密钥;可选项（注：不加访问密钥会存在访问限制）

返回字段
状态：本次API访问状态，如果成功返回“OK”，如果失败返回“失败”

ret：返回属性 - 值对列表，每个对也是一个列表（[attribute，value]）

网址
http://shuyantech.com/api/cndbpedia/avpair?q=**

http://shuyantech.com/api/cndbpedia/avpair?q=**&apikey=**
```

    
## 清单
- [百度云细粒度图像搜索-动物识别API文档](http://ai.baidu.com/docs#/ImageClassify-API/562659ee)
- [阿里云图像识别-动物识别API文档](https://market.aliyun.com/products/57124001/cmapi028672.html?spm=5176.730005-56956004-57124001.productlist.d_cmapi028672.30b53524BbreOu&innerSource=search#sku=yuncode2267200001)
- [百科知识图谱CN-DBpedia](http://kw.fudan.edu.cn/apis/cndbpedia/)
