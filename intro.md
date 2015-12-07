注册
===  

* 请求方式 post
* 请求原因 注册用户
*  post参数 <pre><code>{
"username":sample
"password":"SKJRIOWNFAYUXs",
"where":0,
"headpic":"http://example.com/123.png",
"nickname":"superuser",
"mail":"user@example.com",
"phone":"+8618311112222"
}</code></pre>
* 参数解释  
1. username 用户名 长度 英文4-15
2. password 密码 英文 6-18
3. where   来源 0 app内注册,1 qq,2 weibo, 3weixin.
4. headpic 如果是第三方登陆这里会有用户头像 .png 否则 不会有
5. nickname 用户昵称
6. mail 如果是第三方登陆,这个参数可以没有
7. phone 同上

* 服务端返回格式如下
<pre><code>
{
"respCode":200
"userid":58462186423
}
</code></pre>

登陆
===
* 请求方式 post
* 请求原因 登陆
*  post参数 <pre><code>{
"username":"sample",
"password":"SKJRIOWNFAYUXs"
}</code></pre>
* 参数解释  
1. username 用户名 长度 英文4-15
2. password 密码 英文 6-18

* 服务端返回格式如下
<pre><code>
{
"respCode":200
"userid":58462186423
}
</code></pre>

主页list
===
* 请求方式 GET
* 请求原因  展示主页list
* 请求连接  http://example.com/item/info?page=1&infoSum=10
> 参数说明  
page 第几页  
infoSun 一页有多少item  

* 服务端返回格式如下<pre><code>
{
"respCode":200,//如果返回其他,则说明原因 "errInfo":"服务端异常"
"item":[
{
"itemId":"846513286",
"accessPermission":1,//1低,2中,3高
"pic":"http://example.com/pic/123.png",//此处如果包含图片尺寸已数组形式返回
"movieName":"火星救援",
"movieType":"动作/科幻/剧情",
"movieProducer":"众筹出品人联合出品",
"movieReleaseTime":"2015年12月1日",
"movieSupportSumMoney":"123456",
"movieCurrentlyMoney":"123455",
}
{
"itemId":"846513287",
"pic":"http://example.com/pic/123.png",//此处如果包含图片尺寸已数组形式返回
"movieName":"速度与激情",
"movieType":"动作/科幻/剧情",
"accessPermission":2,//1低,2中,3高
"movieProducer":"众筹出品人联合出品",
"movieReleaseTime":"2015年12月1日",
"movieSupportSumMoney":"123456",
"movieCurrentlyMoney":"123455",
}
]
}
</code></pre>
* 返回参数解释 

 1. movieName: 电影名
 2. movieType: 电影类型,动作/科幻/剧情
 3. accessPermission: 访问权限,低级用户不能访问
 4. movieProducer: 电影出品人.
 5. movieReleaseTime: 开放时间
 6. movieSupportSumMoney 众筹目标金额 人民币
 7. movieCurrentlyMoney 目前已筹集到金额
 8. respCode: 返回码 后期定义
 9. item:返回每个item数组形式 
个人信息
===
* 请求方式 get or post?
* url http://example.com/user?id=123456
* 请求原因 获取用户信息
* 服务器返回参数
<pre><code>
{
   "respCode":200,
    "nickname": "user", 
    "userId": 5458961, 
    "headPic": "http://example.com/123.png", 
    "sysMessage": [
        {
			"sysMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题", 
	   "read": true,
            "detail": "详情"
        }, 
        {
	   "sysMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题1", 
            "detail": "详情1"
        }, 
        {
			"sysMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题2", 
            "detail": "详情2"
        }
    ], 
    "privateMessage": [
        {
			"privateMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题", 
            "detail": "详情"
        }, 
        {
			"privateMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题1", 
            "detail": "详情1"
        }, 
        {
			"privateMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题2", 
            "detail": "详情2"
        }
    ], 
    "groupMessage": [
        {
	"groupMemberNum":999,
	"groupMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题", 
            "detail": "详情"
        }, 
        {
	"groupMemberNum":999,
		"groupMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题1", 
            "detail": "详情1"
        }, 
        {
	"groupMemberNum":999,
	"groupMessageId":5466213,
            "time": "2015年12月12日", 
            "title": "标题2", 
            "detail": "详情2"
        }
    ]
}</code></pre>

* 字段解释: nickname 用户昵称
* userId 用户唯一标识
* headPic 用户头像
* sysMessage 系统信息,
* 
合作信息
===
* 请求方式 get
* 请求原因 更新合作信息数据.
* url http://example.com/getpartnerinfo
<pre><code>{
"serviceHotline":4008008888,
"partnerHotLine":13088881111,
"onlineChat":13800001111
}
</code></pre>

设置
===
* 请求方式 get
* 请求原因 获取设置中的推荐app和其他相关数据
* url http://example.com/getappinfo
<pre><code>{
"down1":"http://example.com/test",
"down2":"http://example.com/test1",
...
"about":"blabla"
}</code></pre>

退出
===
* 请求方式 get
* 请求原因 使用户变成离线状态.
* url http://example.com/userquit?userId=1234
* 返回 <pre><code>{
"respCode":"200"
}</code></pre>

帮助
===
* 请求方式 get
* 请求原因 获取帮助静态页
* url http://example.com/gethelp  //如果此处不同用户对应不同的帮助详情 就  userId
* 返回 <pre><code>{
"help1":[
{
"title":"如何使用邀请码",
"answer":"blabla"
}
{
"title":" 如何参与项目",
"answer":"blabla"
}
...
]
}</code></pre>
* 解释 各种 QA 已数组形式返回,一个QA对应一个对象即{}
detail
===
* 请求方式 get
* 请求原因 获取详情页
* url http://example.com/detail?itemId=123456
* 返回 
<pre><code>
{
    "itemId": 123456, 
    "userId": 5458961, 
    "accessPermission": "3",
	"video":"http://example.com/123.mp4"
    "bannerNum": 4, 
	"movieName":"火星救援",
	"producterName":"二十世纪集福寺电影公司",
	"movieTxt","blabla很多字",
	"openDate":"2015年12月7日",
    "banner": [
        {
            "picUrl":"http://example.com/123.png",
			"height":"230px",
			"width":"300px"
        }, 
        {
            "picUrl":"http://example.com/122.png",
			"height":"230px",
			"width":"300px"
        }, 
		...
    ], 
	"supportMoney":"1324567",
	"supportPeople":"132456",
	"totalMoney":"222222",
	"deadline":"2015年12月30日",
	"team":[
		{
		"name":"阿里若渴",
		"headPic":"http://example.com/123.png"
		}
		{
		"name":"阿里若渴",
		"headPic":"http://example.com/123.png"
		}
		{
		"name":"阿里若渴",
		"headPic":"http://example.com/123.png"
		}
		...
	]
    "support": [
        {
			"support":1500,
            "supportTitle":"blabla",
            "supportDetail": "blabla", 
        }, 
        {
			"support":2000,
            "supportTitle":"blabla",
            "supportDetail": "blabla", 
        }, 
		{
			"support":2500,
            "supportTitle":"blabla",
            "supportDetail": "blabla", 
        }
    ], 
    "dynamic": [
        {
			"userId":5466213,
            "upvote":"160",
			"time": "2015年12月12日", 
            "title": "标题", 
            "detail": "详情",
			"location":"上海",
			"hour":"3小时前",
			"pic":[
			{"url1":"http://example.com/123.png"}
			{"url1":"http://example.com/123.png"}
			{"url1":"http://example.com/123.png"}
			..
			]
        }, 
       {
			"userId":54662123,
            "upvote":"160",
			"time": "2015年12月12日", 
            "title": "标题", 
            "detail": "详情",
			"location":"上海",
			"hour":"3小时前",
			"pic":[
			{"url1":"http://example.com/123.png"}
			{"url1":"http://example.com/123.png"}
			{"url1":"http://example.com/123.png"}
			..
			]
        }, 
		....
    ]
}
</code></pre>
