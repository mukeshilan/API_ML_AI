# product requirements
发布日期 | 2018年11月25日
---|---
主题 | 动物识别
文件现状 | 进行中
作者 | 陈丽媛
设计师 | 陈丽媛
开发者 | 陈丽媛
测试者 | 陈丽媛

# 目标
- 根据动物的实拍照片帮助用户识别动物，解释动物的品种、形态特等信息。

# 背景和战略契合处
- 用户在遇到陌生的动物会想要了解它的名字、种类等信息，这时候需要一个能识别的工具来帮助用户。
- 目前市场上的动物识别软件分为几种：
    - 全能识别，一个软件能识别好几种物体，动物、植物、车型等，如：“全能识别APP”，但是这个识别软件只能显示名称，不能显示更多详细信息。“拍照识物APP”：广告多且明显，识别效果一般，查看详细信息时会自动打开手机浏览器跳至“百度百科”。“智能图像识别APP”:有广告弹出，显示详细信息时页面显示为“百度百科”，每次识别后都会有广告弹出，且有不能跳转的可能。
    - 只识别动物。“动物守护者APP”：一般用户不能拍照识别，只能根据动物特征来识别，且只能识别国家级保护动物，可用性不强。
    - 小程序识别：只能显示名称，且准确率不高。

# 假定
- 所识别的动物外表未经过人为改变。
- 拍摄的照片不是虚构的。
- 用户使用时摄像机能够正常使用。
- 用户拍摄的照片足够清晰。

# 需求
标题 | 用户案例 | 重要程度 | 笔记
-----|----------|----------|-----
辨别动物品种 | 小明某天看到一只宠物狗，但是分不清它的品种是金毛还是拉布拉多 | 重要 | 动物识别
科普 | 大明带着小明外出游玩，看到一只昆虫，小明问大明昆虫这是什么动物，大明无法回答 | 重要 | 儿童科普
交流 | 用户识别后觉得有误或图片不能够被识别 |次重要 | 动物识别
游戏 | 用户觉得只能APP只能识别动物太单一了，没有乐趣 |次重要 | 用户粘合度

# 使用者交互及设计
- 架构
![image](https://note.youdao.com/yws/api/personal/file/C450FAD3DDF244F696169C3EDC75BE5C?method=download&shareKey=52527f7e715be22a7c3dee26e19cc408)
# 问题
问题 | 结果
---|---
如何指导用户拍出更能识别的动物图片|给用户展示拍照图例提示用户
不能确认图片上的动物|列出可能是此动物的信息，提示用户换角度再次拍摄进行识别
识别特征不明显的动物（如：杂交犬类）| 显示大的类（例如：科：犬科）

# 加值宣言
- 拍照或上传照片即可识别出各种动物名称、详细信息。
- 设定识别一定量动物的时候可以解锁不同的虚拟宠物。

# 核心价值
- 识别上传的动物图片，返回该动物的名称、详细信息。

# 核心价值与用户痛点
- 喜欢动物的人或者户外爱好者看到不知名的动物会产生好奇心，但是又不知道这种动物叫什么，也没有什么工具能够证明。
- 家长教育孩子时偶尔会遇到不知名的动物，无法给孩子进行教育。

# 人工智能概率性与用户痛点
- 动物识别正确率在90%以上，适合非专业人群日常生活使用。
# 交互及界面设计
- [界面设计](https://mukeshilan.github.io/animal)


# 需求列表与人工智能API加值
- 图像分类
    - 阿里云-【图像识别OCR】动物识别：识别准确率高达90%以上
- 知识图谱
    - 百科知识图谱CN-DBpedia：CN-DBpedia是由复旦大学知识工场实验室研发并维护的大规模通用领域结构化百科，其前身是复旦GDM中文知识图谱，是国内最早推出的也是目前最大规模的开放百科中文知识图谱，涵盖数千万实体和数亿级的关系，相关知识服务API累计调用量已达6亿次。
# 产品使用关键AI或机器学习之API的输出入展示
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
# 将做
- 通过录制动物的声音来确定动物的类型。
    
## 清单
[界面设计](https://mukeshilan.github.io/animal)
- [阿里云图像识别-动物识别API文档](https://market.aliyun.com/products/57124001/cmapi028672.html?spm=5176.730005-56956004-57124001.productlist.d_cmapi028672.30b53524BbreOu&innerSource=search#sku=yuncode2267200001)
- [百科知识图谱CN-DBpedia](http://kw.fudan.edu.cn/apis/cndbpedia/)
