#易企秀H5渲染引擎

version 1.0
    @author 袁飞
    @date 2019年10月26日

# 项目介绍
该引擎是用来渲染易企秀H5编辑器生成的作品。目前易企秀H5编辑器的作品只能让编辑器提供的链接观看，而该引擎可以摆脱链接的束缚，
从而在你自己的网页上显示作品。

# 项目引入
需要引入两个文件(一个css, 一个js)

```
<link href="//lib.eqh5.com/@eqxiu/h5View/1.0.0/h5View-1.0.0.css" rel="stylesheet"></head>
<script type="text/javascript" src="//lib.eqh5.com/@eqxiu/h5View/1.0.0/h5View-1.0.0.js"></script>
```

# 项目用法
该项目依赖jquery， 请在引入改文件之前，先引入jquery。
引入文件后，在全局会有一个变量：EqxH5View。可以new这个对象，并执行start方法就可以了。
```javascript
    let config = {
        code: 'z7aPC7XK',
        $dom: $('.nr'),
        sceneInfo: {},
        sceneList: [],
        wx: {
            nickname: 'philip'
        },
        lastPage: true,
        lastFlip: function () {
            console.log('aa');
        },
        // disableComp: [2, 3, 'v']
    }
    let eqxH5View = new EqxH5View(config);
    eqxH5View.start();
```
在new这个start对象时，你需要提供配置信息,配置的参数信息如下。

<table border="1">
    <tbody>
    <tr>
        <th>参数</th>
        <th>类型</th>
        <th>是否必须</th>
        <th>含义</th>
    </tr>
    <tr>
        <td>code</td>
        <td>string</td>
        <td>Y</td>
        <td>需要展示场景的code</td>
    </tr>
    <tr>
        <td>$dom</td>
        <td>Jquery 对象</td>
        <td>Y</td>
        <td>场景内容所放的容器</td>
    </tr>
    <tr>
        <td>sceneInfo</td>
        <td>json</td>
        <td>N</td>
        <td>场景基本信息，需要和sceneList配合使用。可以根据需求，只显示场景特定几页。具体请看sceneList含义</td>
    </tr>
    <tr>
        <td>sceneList</td>
        <td>array</td>
        <td>N</td>
        <td>场景页的数据，需要和sceneInfo配合使用。当既添加sceneInfo和sceneInfo参数，会显示sceneList里有的场景页数据，而不是场景所有页。</td>
    </tr>
    <tr>
        <td>wx</td>
        <td>Object</td>
        <td>N</td>
        <td>通过微信授权获得的用户的信息（比如：nickname, headimgurl...）, 提供这个信息后，微信头像和妮称组件就会显示用户的，否者为默认的</td>
    </tr>
    <tr>
        <td>lastPage</td>
        <td>Booleans</td>
        <td>N</td>
        <td>最后广告页是否显示， 默认是不显示（false），显示设置true</td>
    </tr>
    <tr>
        <td>lastFlip</td>
        <td>Function</td>
        <td>N</td>
        <td>回调函数，当页面翻页到最后一页后，再往下翻页时触发。默认翻到第一页，如果设置回调，就不会翻到第一页，而是触发传递进来的回调。</td>
    </tr>
    <tr>
        <td>disableComp</td>
        <td>Array</td>
        <td>N</td>
        <td>设置不想展示的组件，数组里放置组件的类型</td>
    </tr>
    </tbody>
</table>



#附录
组件类型列表， 有几个组件暂不支持（组件名称后面标注了），还有组件有防刷单功能的设置项，也暂不可用。

```javascript
    // 画中画长按按钮
    16: 'EqxPipButton',
    // 1爆款文本
    1: 'EqxHotNewText',
    // 照片墙
    13: 'EqxPhotoWall',
    // 新文本
    7: 'EqxNewText',
    // 秀字体变为普通文本
    2: 'EqxText',
    x: 'EqxText',
    // 背景
    3: 'EqxBackground',
    // 图片
    4: 'EqxImage',
    // 电话
    8: 'EqxTelephone',
    // 红包  -- 不支持
    9: 'EqxRedPacket',
    // 随机事件组件
    10: 'EqxRandomContent',
    // 打赏  -- 不支持
    11: 'EqxReward',
    // 留言板
    b: 'EqxComment',
    // 图形
    h: 'EqxShape',
    // 计数组件, 防刷单组件
    i: 'EqxCount',
    // 链接组件
    l: 'EqxLink',
    // 图表
    t: 'EqxChart',
    // 外链视频
    v: 'EqxVideo',
    // 视频
    o: 'EqxInteractiveVideo',
    // 图集
    p: 'EqxImageSlider',
    // 地图
    m: 'EqxMap',
    // 随机组件
    n: 'EqxRandom',
    // 音效
    s: 'EqxSound',
    // 阅读量
    d: 'EqxPv',
    // 倒计时
    e: 'EqxDownTime',
    // 正计时
    f: 'EqxUpTime',

    // ======== form ================
    // 上传图片
    upload: 'EqxUploadImages',
    // 评分组件
    a: 'EqxScore',
    // 多选
    c: 'EqxCheckbox',
    // 单选
    r: 'EqxRadio',
    // 下拉列表
    z: 'EqxDropDownList',
    // 输入框
    5: 'EqxInput',
    // 姓名
    501: 'EqxInput',
    // *手机*
    502: 'EqxInputPhone',
    // *邮箱*
    503: 'EqxInputEmail',
    // 文本
    504: 'EqxInput',
    // 提交表单 防刷单组件
    6: 'EqxSubmitButton',
    601: 'EqxSubmitButton',
    // 短信验证
    12: 'EqxSMS',

    //  =========== 微信 ===============

    // 微信昵称
    201: 'EqxWxNickName',
    // 微信替换图片
    401: 'EqxWxProfile',
    // 微信上传图片
    403: 'EqxWxUploadImage',
    // 微信播放语音  -- 不支持
    w01: 'EqxWxSoundPlay',
    // 微信录音  -- 不支持
    w02: 'EqxWxSoundRecord',
    // 微信图片投票  -- 不支持
    j: 'EqxImgVote',
    // 微信文字投票  -- 不支持
    k: 'EqxTextVote',

    // ====== 重力感应 ====
    q: 'EqxGravity',
    // 画板  -- 不支持
    u: 'EqxDrawingBoard',

    // ======日期组件 ====
    14: 'EqxDate',

    // 微信卡券  -- 不支持
    17: 'EqxWeChatCard',
    // ======互动营销组件 ====
    // 转盘抽奖  -- 不支持
    18: 'EqxTurntable',
    // 砸金蛋  -- 不支持
    19: 'EqxSmashEgg',
    // 一刮千金  -- 不支持
    20: 'EqxScratchcard',
    // 新红包组件  -- 不支持
    21: 'EqxRedPackets',
    // 幸运九宫格 -- 不支持
    22: 'EqxNineSquare',
    // 二维码
    23: 'EqxQrcode',
    // 点击截图按钮
    24: 'EqxLongTouchSavePicButton',
    // 艺术字
    25: 'EqxWordArt',
    // 自说字画
    26: 'EqxSpeechRecognition',
    // 立体魔方
    27: 'EqxMagicCube',
    // 自定义表单
    29: 'EqxFormRandom',
    // 动态数字
    30: 'EqxDynamicNumber'
```