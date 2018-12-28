## 产品需求文档
发布日期 | 2018年11月25日
---|---
主题 | 动物世界
文件现状 | 进行中
作者 | 陈丽媛

## 目标
- 根据动物的实拍照片帮助用户识别动物，解释动物的品种、形态特征等、可信度。
- 用户识别后可分享至“社区”板块，在“社区”板块还可进行用户自发组织的动物分辨，用户确认后可将信息反馈给APP。
- 设置“萌宠”功能，用户识别一定数量后可升级。

## 背景和战略契合处
- 用户在遇到陌生的动物会想要了解它的名字、种类等信息，这时候需要一个能识别的工具来帮助用户。
- 目前市场上的动物识别软件分为几种：
    - 全能识别，一个软件能识别好几种物体，动物、植物、车型等，如：“全能识别APP”，但是这个识别软件只能显示名称，不能显示更多详细信息。“拍照识物APP”：广告多且明显，识别效果一般，查看详细信息时会自动打开手机浏览器跳至“百度百科”。“智能图像识别APP”:有广告弹出，显示详细信息时页面显示为“百度百科”，每次识别后都会有广告弹出，且有不能跳转的可能。
    - 只识别动物。“动物守护者APP”：一般用户不能拍照识别，只能根据动物特征来识别，且只能识别国家级保护动物，可用性不强。
    - 小程序识别：只能显示名称，且准确率不高。
## 加值宣言
- 用户可根据识别结果进行更正反馈，APP收集足够的反馈后可进行定制化图像识别再应用到APP中，从而提高识别率。
- 设定识别一定量动物的时候可以解锁不同的虚拟宠物。

## 核心价值
- 识别上传的动物图片，返回该动物的名称、详细信息及可信度。

## 核心价值与用户痛点
- 喜欢动物的人或者户外爱好者看到不知名的动物会产生好奇心，但是又不知道这种动物叫什么，现有的APP却满足不了用户需求。
- 家长教育孩子时偶尔会遇到不知名的动物，无法给孩子进行教育。

## 人工智能概率性与用户痛点
- 显示动物识别可信度，适合非专业人群日常生活使用。
- 识别后可行度过低，用户可将结果分享到APP，其他用户可对此动物进行辨别，用户可将辨别结果反馈给APP。
- 经过试验，此动物识别能够满足普通用户的需求。
    - 原图
![image](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E5%8E%9F%E5%9B%BE.JPG) 

    - 裁剪后
![image](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E7%BC%BA%E5%A4%B1.JPG)

    - 模糊化
![image](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E6%A8%A1%E7%B3%8A.JPG)

## 假定
- 所识别的动物外表未经过人为改变。
- 拍摄的照片不是虚构的。
- 用户拍摄的照片足够清晰。

## 需求分析
标题 | 用户案例 | 重要程度 | 笔记
-----|----------|----------|-----
辨别科普 | 钱女士带着小钱外出游玩，看到一只昆虫，小钱问钱女士昆虫的名字，钱女士无法回答 | 重要 | 动物识别
交流 | 用户识别后觉得有误或图片不能够被识别，可以将识别结果分享出去，请其他用户一起分析得出正确结果 |重要 | 动物识别
游戏 | 用户觉得只能APP只能识别动物太单一了，没有乐趣 |次重要 | 用户粘合度

# 问题
问题 | 结果
---|---
如何指导用户拍出更能识别的动物图片|首次使用，给用户展示拍照图例提示用户
不能确认图片上的动物|列出可能是此动物的信息，提示用户换角度再次拍摄进行识别
一张图片中超过一种动物 | 目前不能识别包含一种动物以上的图片，需用户重新拍摄或对图片进行处理

## 使用者交互及设计
- 产品结构图
![image](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E5%8A%A8%E7%89%A9%E4%B8%96%E7%95%8C.png)

- [界面设计](https://mukeshilan.github.io/animal/)
    - 首页

![首页](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E9%A6%96%E9%A1%B5.JPG)
    - 识别过程

![识别过程](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E8%AF%86%E5%88%AB%E8%BF%87%E7%A8%8B.JPG)
    - 社区

![社区](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E7%A4%BE%E5%8C%BA.JPG)
    - 我的

![image](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E6%88%91%E7%9A%84.JPG)


## 需求列表与人工智能API加值
- 图像分类
    - 百度云-细粒度图像识别—动物识别：具有免费调用额度的接口。
- 知识图谱
    - 百科知识图谱CN-DBpedia：CN-DBpedia是由复旦大学知识工场实验室研发并维护的大规模通用领域结构化百科，其前身是复旦GDM中文知识图谱，是国内最早推出的也是目前最大规模的开放百科中文知识图谱，涵盖数千万实体和数亿级的关系，相关知识服务API累计调用量已达6亿次。
## 产品使用关键AI或机器学习之API的输出入展示
- 百度云图像识别-动物识别API[（API文档）](https://cloud.baidu.com/doc/IMAGERECOGNITION/ImageClassify-API.html#.3F.A6.A9.4B.62.0C.D2.FE.EB.ED.32.41.D8.9D.22.26)
    - 输入：图片
    - 输出：物种类型、可信度

```
#第一步：获取access_token

import urllib.request
 
# client_id 为官网获取的AK， client_secret 为官网获取的SK
host = 'https://aip.baidubce.com/oauth/2.0/token?grant_type=client_credentials&client_id=QC2ltFaISK70gIN3QBbO1KUd&client_secret=RYNRSaF0fQPEx6w9ABMoMVzUsInTleIm'
request = urllib.request.Request(host)
request.add_header('Content-Type', 'application/json; charset=UTF-8')
response = urllib.request.urlopen(request)
content = response.read()
if (content):
    print(content)
```

```
#第二步：输入图片（图例为大熊猫）

import base64
import urllib.parse
import urllib.request

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v1/animal"
 
#二进制方式打开图片文件
f = open('C:/Users/asus/Desktop/1.jpg', 'rb')
img = base64.b64encode(f.read())
 
params = {"image":img,"top_num":6}
params = urllib.parse.urlencode(params).encode(encoding='UTF8')
 
access_token = '24.934b0693ee1af59c82c483d1e78dd0a1.2592000.1547880347.282335-15018916'
request_url = request_url + "?access_token=" + access_token
request = urllib.request.Request(url=request_url, data=params)
request.add_header('Content-Type', 'application/x-www-form-urlencoded')
response = urllib.request.urlopen(request)
content = response.read()
if content:
    print(bytes(content).decode('utf-8'))
```


```
#输出结果
{"log_id": 2052725290618052564, "result": [{"score": "0.898347", "name": "国宝大熊猫"}, {"score": "0.027174", "name": "圆仔"}, {"score": "0.0249033", "name": "秦岭四宝"}, {"score": "0.0139097", "name": "棕色大熊猫"}, {"score": "0.0117152", "name": "团团圆圆"}, {"score": "0.00114086", "name": "小熊猫"}]}
```

- 百科知识图谱CN-DBpedia（[API文档](http://kw.fudan.edu.cn/apis/cndbpedia/)）
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
## API比较分析
- [阿里云动物识别](https://market.aliyun.com/products/57124001/cmapi028672.html?spm=5176.11065268.1996646101.searchclickresult.2cda551buSWWxd#sku=yuncode2267200001)：
    - 优点：1.输出结果包括动物名称和类型；2.识别准确率高达90%以上；
    - 缺点：价格过高
![阿里云API价格](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E9%98%BF%E9%87%8C%E4%BA%91API%E4%BB%B7%E6%A0%BC.JPG)

- 百度云-细粒度图像识别—动物识别
    - 优点：1.输出结果包括动物名称、可信度；2.价格便宜
    - 缺点：可信度过低会给用户不好的体验。
    
![百度云API价格](https://raw.githubusercontent.com/mukeshilan/-Animal_recognition_picture/master/%E7%99%BE%E5%BA%A6%E4%BA%91API%E4%BB%B7%E6%A0%BC.JPG)

- 百科知识图谱CN-DBpedia
    - 优点：内容丰富，CN-DBpedia提供全套API，并且免费开放使用
    - 缺点：商用需进行许可，大规模调用需联系对方。

## 使用后风险报告
- 若“动物世界APP”不被知识图谱CN-DBpedia支持，则使用百度百科数据（2018年7月5日开放）。
- 使用百度云图像识别-动物识别API识别，识别率过低的动物的信息和反馈，通过定制化图像识别API生成定制化API，进行APP升级，提高APP的识别正确率。

## 将做
- 通过录制动物的声音来确定动物的类型。
- 收集来自反馈的覆盖不同光线、不同角度、不同背景的样本图片后，根据进行定制化图像识别提高APP识别率。[（定制化图像识别API)](http://ai.baidu.com/forum/topic/show/593353)
 
   
## 清单
- [界面设计](https://mukeshilan.github.io/animal/)
- [百度云图像识别-动物识别API](https://cloud.baidu.com/doc/IMAGERECOGNITION/ImageClassify-API.html#.3F.A6.A9.4B.62.0C.D2.FE.EB.ED.32.41.D8.9D.22.26)
- [百科知识图谱CN-DBpedia](http://kw.fudan.edu.cn/apis/cndbpedia/)
- [阿里云图像识别-动物识别API文档](https://market.aliyun.com/products/57124001/cmapi028672.html?spm=5176.730005-56956004-57124001.productlist.d_cmapi028672.30b53524BbreOu&innerSource=search#sku=yuncode2267200001)
- [定制化图像识别API](http://ai.baidu.com/forum/topic/show/593353)
