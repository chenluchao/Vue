#Vue 框架

##1.Vue 基础
###1.1 基础

1.vue 介绍

    q.什么是 vue?

        vue 是前端 js 框架, 一个用户构建用户 UI 界面的框架

    q.区分框架和库
        库: jquery,zepto,swiper,iscroll,lazyload.....
            库是一个系列功能的集合, 通过调用库中函数或者使用对象实现我们的功能
        框架: bootstrap,vue,react,angular    微信小程序(数据绑定机制)
            框架定义了一些开发规则,提供了程序的骨架, 需要按照框架的规则去填充我们的逻辑代码

    q.关于vue
        vue的作者: 尤雨溪

        vue中文官网: https://cn.vuejs.org/
        vue中文官方教程: https://cn.vuejs.org/v2/guide/
        vue api手册: https://cn.vuejs.org/v2/api/


    q.vue的优点和缺点
        优点: (1)vue相对其他框架学习简单,使用简单,适合入门
            (2)vue适合多个交互功能,大中型的项目
            (3)vue开发模式是组件式开发, 适合重复开发, 功能都变成组件, 以后项目直接用
            (4)适合做后台管理系统
            .....

        缺点:
            (1)具有学习成本的,完成一个功能, js简单实现了, vue重新学习如何写
            (2)经历一思维方式的转变(vue一般不直接操作dom)
            (3)不适合开发需要进行SEO优化的项目
            .....

    q.vue的版本
        早期版本 0.11和0.12 试验品
        上一个版本 1.0版本
        最新的版本 2.0版本(当前使用版本)

2.环境搭建和 helloworld

    q.运行vue代码, 如何运行
        代码中添加vue.js这个文件, 添加之后写vue代码
        以后,脚手架需要通过 import导入使用


    q.写一个helloworld
        定义一个div,设置id=app
        导入vue.js
        定义vue实例

3.数据绑定(vue 的核心)

    q.js原生的操作数据数据的方式?
        以前js操作数据, 如果js的值显示到界面中  tag.innerHTML = "hello"
        如果数据变动了,   tag.innerHTML = "world"

        当输入框的中数据, 在js获取  onchange="dealChange", 事件处理函数中获取数据

        ["zhang","li","wangwu","maliu]   =>   <div><div>zhang</div><div>li</div><div>wangwu</div></div>

    q.什么是数据绑定机制

        界面中js中部分数据通过一种机制显示到界面上, 当数据变化,界面同步变化,或者界面变化,数据同步变化


    q.举个数据绑定的例子

        vue实例中data定义的变量, 最后会绑定的vue实例上(不是vue的data中), vue实例中直接通过this.msg操作数据, 实例之外通过 app.msg修改

        vue添加click事件:  vue通过@click绑定事件, 对应的函数要放在vue实例的methods对象中


    q.vue中支持双向数据绑定

        单向数据绑定: 微信的, data数据变了,显示就变了,  输入框输入变了, 对应的数据手工去改动,让他变

        双向数据绑定: 通过v-model这个指令和建立 一个变量和输入框双向数据绑定
            数据变 => 界面变
            输入变 => 数据也变

    q.v-model是什么,怎么用?
        v-model是vue中的一个指令, 起始就是html中自定义属性, vue中有特殊意义
        语法: v-model="变量名"
        注意: 变量名两边不加{{}}

4.各种数据渲染(如何把不同类型的数据显示到界面上)

    q.如何实现普通渲染

        格式1: data中普通变量, 直接在界面上通过 {{msg}} 去显示
        格式2: 通过v-text去显示
            <div v-text="msg"></div>

    q.如何实现属性渲染
        想要把data中的变量放到标签的属性上, 使用v-bind指令
        格式1: <a v-bind:href="url1"></a>
        格式2: <a :href="url1"></a>


        注意: 以后如果见到了 :href形式, 反应过来, 是简写


    q.如何实现样式渲染
        想要把data中样式数据,设置给标签, 使用指令还是 v-bind:style,  有几种格式

        格式1:  <div :style="s1"></div>
            要求: s1是个data中定义的对象, 这个对象中是样式的定义
            注意: 类似一个font-size不要直接写, 要写成 fontSize或者"font-size"



    q.如何实现class渲染
        如果在data定义了类名, 如何在vue的视图中使用这些类名

        第一种形式: html自带形式
        html:  <div class="s1 s2"></div>

        第二种形式: :class的值只能是字符串,或者数组, 或者对象
        vue:  <div :class=" 's1 s2' "></div>
        vue:  <div :class=" ['s1','s2'] "></div>
        第四种形式: :class的值是个对象, 这个对象中键值对中值的结果为真的样式会应用
        vue:  <div :class=" {'s1':true,'s2':false} "></div>

        疑问: 好好的html的样式写挺好的, 为啥要用这些???
            把类名这些数据放在data里, 修改了数据了之后,界面会自动改变


    q.如何实现条件渲染
        想要实现一个div要么存在要么不存在, 效果要么显示要么隐藏

        格式:  v-if="表达式"
            这个表达式为真, vue就会把标签插入到dom显示
            否则不会插入到dom中


    q.如何实现循环渲染
        数据里面有个数组, 我们要把数组中每个元素显示出来?

        格式: v-for="(item,index) for list" :key="index"
            list是个数组, 名字是数组名
            item是每个数组中每个对象, index是索引序号,从0开始,个数为10, index:0~9

        注意1: :key可以不加, 有时候会有警告
        注意2: (item,index)可以简化为item
        注意3: 能遍历的除了数组之外,还能遍历对象

        项目: 遍历显示最多的数组中全部是对象


    q.如何实现输入框双向绑定?

        想要让输入框中的值, 同步到data的变量中, 使用v-model这个指令

        效果1: 当变量改变, 输入框中显示的值改变
        效果2: 当输入的值改变, 变量就变为对应的值


    q.如何显示或隐藏标签

        显示和v-if的区别
            显示和隐藏使用指令v-show
            v-if控制一个标签是否插入到节点中


        v-if为假, 对应的标签移除到dom之外
            为真, 插入到dom之中

        v-show为假, 标签添加样式 style="display:none"
            为真, 去除这个样式

5.表达式

    q. {{}} v-if中放的都是表达式, 哪些变量能用, 哪些函数能用, 哪些不能用?

        能放的
            数学表达式
            字符串表达式
            data中定义的变量
            methods定义的函数,注意函数能带参数
            js自带的函数,例如Math.abs()

        不能放
            不在data中定义的变量
            不在methods定义函数(排除系统函数)

6.事件处理

    q.如何实现点击的事件处理
        单击  @click="dealClick"
        双击 @dblclick="dealClick"

    q.如何实现鼠标的事件处理
        进入 @mouseenter="dealEnter($event)"
        移动 @mousemove="dealMove($event)"
        离开 @mouseleave="dealLeave($event)"

        注意: 如果事件处理函数中想要获取事件对象和里面的数据, 添加一个参数$event, 可以不加

    q.如何实现键盘的事件处理
        @keydown="dealDown"
        @keyup="dealUp"
        @keypress="dealPress"
        @change="dealChange"
        @focus="dealFocus"
        @blur="dealBlur"

    q.事件处理的值除了能是函数之外,能不能放别的?
        vue中处理事件除了能放函数, 还能直接放表达式, 直接去修改数据
        案例:  @click="isShow=!isShow"

7.计算属性

    q.什么是计算属性, 作用是什么?
        data中添加的可以认为是普通属性, 有些属性它的值根据普通属性计算出来的,就叫计算属性

        定义: 一个计算属性不是直接定义在data中, 而是依赖其他的属性的值,通过其他属性的值计算出来
        举例: 购物车    总价 = 商品1价格*数量 + 商品2价格*数量+ 商品3价格*数量

    q.写一个依赖两个数字的属性, 这个属性是两数之和

        定义: 在vue实例中添加 computed:{}, 里面加入函数, 函数名就是属性名, 内部返回对应值
        使用: 当做普通的属性使用, 但是不能修改,只能获取

        注意: 当计算属性依赖的属性变化的时候, 计算属性的值会同步变化(很有用)

8.生命周期(实例)

    微信小程序
        一个页面加载
            onLoad -> onShow -> onReady

        一个界面销毁
            onUnload

        A界面navigator到B界面
            A  onHide()

        B界面返回到A界面
            B onUnload

        onPullDownRefresh
            下拉执行

        onReachBottom
            上拉执行

        onShareAppMessage
            转发执行

    vue
        一个实例有4个过程
            创建 create
                beforeCreate
                created

            加载 mount
                beforeMount
                mounted

            更新(有的时候可能没有) update
                beforeUpdate
                updated

            销毁 destroy (组件v-if="false"会执行)
                beforeDestroy
                destroyed

    q.一个实例从生成到更新有什么过程, 其中数据和view什么时候是可用的
        create之前 $data没有生成, $el也没有生成
            啥也干不了
        created之后  $data生成了, 可以操作数据了

        mount之前   $el就是模板数据, 不是dom数据, view模板没有变成dom,没有加载

        mount之后    $el就是显示dom, 是dom, 界面就可以操作了


    q.常用的事件处理函数是哪个?
        created最常用,  往往初始化数据
        mounted 可以操作html, 往往也是显示了

9.组件 \*\*\* [开发非常重要]

    简介
        q.什么组件,他的作用是什么?
            vue的组件一系列功能封装, 把一个功能所有html和css和js封装在了一个组件, 使用类似于一个标签
            理解: 写好了组件, 其他地方使用组件最简单就是引入组件, 然后添加一个标签
            特点: 前人栽树,后人乘凉

            类似于函数, 函数把很多代码封装到了函数中, 使用的直接调用一句函数就行了

    基本使用
        q.如何定义组件?
            通过 Vue.component函数定义

            var Hello = Vue.component(组件名, 对象-初始化选项)

            名字规则:
            //组件名字: 建议全部小写,中间用-分割, 最好不要用驼峰式
    		//前面返回的这个值很少用, 一般不写
    		//template参数必须定义,不定义报错, 里面写html代码
    		//特别注意:
    		//	如果名字定义全小写, 用的时候直接用
    		//	如果名字驼峰式, 用的是全小写和-形式
            //特别注意:
    		//	要定义放在实例的前面
    组件data
        q.实例有data属性, 能存储数据, 组件内部能存储数据
            可以的, 组件可以添加data属性, 注意data属性格式与组件不一致
            格式: 应该是一个返回对象的函数
                data(){
                    return{

                    }
                }
        q.组件内能定义函数吗?
            组件内直接添加methods属性,定义的函数,在组件内部直接使用

    组件的参数
        q.如何的参数是什么,干什么用?
            就像函数有参数有参数一样, 函数需要处理不同的数据, 把数据通过参数传入函数

            组件需要显示不同的数据, 可以可以通过属性给组件添加参数, 让组件显示不同的数据

        q.参数名应该注意什么?
            //参数名
    		//props可以添加多个属性, 每个属性名规则必须是一个变量名, 因为要在{{}}使用
    		//一个变量全小写, 组价使用直接写, 组件外部传参直接写
    		//特殊:
    		//	如果一个变量是驼峰式, 组件内部直接使用, 组件传参时候要用小写加-形式


        q.参数使用注意什么?
            组件内部不要修改参数, 不能修改参数, 但是组件外部可以修改传入的参数
            规则: 单向数据流通

            常见解决: 组件内部要修改参数的话, 定义一个data中的变量, 这个变量的值变为参数的值
                    然后直接修改变量就行了, 不要修改参数, [为什么, 父组件会修改参数]



    组件间传递数据
        q.组件之间传递数据的方式有哪些?
            父组件=>子组件
                使用属性props
            父组件=>子组件(动态)
                使用属性props, 传参绑定数据传值  :title
            子组件=>父组件
                使用自定义事件, 组件内部触发事件 this.$emit("mye"), 组件@mye=""
            跨组件传递
                单独定义一个vue实例, 通过这个实例和自定义事件实现传递
            vuex简单介绍
                应用状态管理工具, 实现更多高级操作

        q.子组件=>父组件使用自定义事件具体如何传值?
            S1: 组件内部触发一个自定义事件
                //触发一个自定义事件
                //$emit是vue提供的函数,功能是触发一个自定义事件
                //参数1: 事件名, 规则符合普通变量
                //参数2: 想要传递的参数
                this.$emit("mychange", this.in_count);

            S2: 组件外部添加组件的地方, 实现事件的监听
                @mychange="dealChange"


            S3: 组件外部methods中实现事件处理函数
                    dealChange(c){
                        //事件处理函数执行的, 表示组件内部触发了事件, 参数接收数据
                    }

        q.跨组件的数据传递(之间没啥关系,关系有, 太远)
            选择1 vue实例, eventBus
            选择2 vuex vue提供状态管理工具

        q.eventBus如何使用?
            //Step1: 通过新的vue实例, 叫做事件总线
    		var eventBus = new Vue();

            //Step2: 组件A - 触发一个事件
            //事件名: mychange
            //事件附带的值: this.count
            eventBus.$emit("mychange", this.count);

            //Step3: 组件B - 监听mychange事件的触发
            //参数1: mychange, 需要监听的事件名
            //参数2: 事件触发了之后, 执行的事件处理函数
            //var self = this;
            eventBus.$on("mychange", c => {
                console.log("c = " + c);

                //total-price组件内的count = 传入的值
                this.count = c;
            });


    组件的生命周期
        destroy

10.插件 [开发非常重要]

    插件的定义
        q.什么是插件, 插件能做什么?
            vue上想要添加一个全局的功能, 使用插件去添加这个功能

            能做的给vue全局添加方法和属性, 全局添加各种资源(指令.....)

        q.如何定义一个插件
            定义一个空对象, 添加一个函数叫做install(函数名固定), install添加参数Vue,options
                实现这个函数就行了




    插件的使用
        q.插件如何使用?
            在vue实例定义前引入插件, 然后使用 Vue.use(插件对象)

            代码直接使用插件的功能


    项目/脚手架使用插件的方式什么样的?
        cmd:        npm install axios --save-dev
        main.js:    import axios;
                    Vue.use(axios)
        使用插件     this.$http.get()

11.watch 数据监听(官网叫侦听器)

    q.watch是什么, 实现什么功能, 解决什么问题?
        watch是数据监控, 有个时候, 想要在一个数据变化之后,
        执行某个操作,通过vue的watch机制去监听某个数据


    q.watch如何使用
        实例或者组件中添加一个属性watch, 值是一个对象, 对象添加多个函数,
        函数名就是监听的变量的名字, 结果当数据变化, 对应的函数就会执行

        格式:
            watch:{
                变量名(新的值, 旧的值){

                }
            }

12.网络数据下载

    网络请求
        GET请求
            <form action='deal.php' method='get'>
            </form>
            特点1: 参数直接放在url中, 服务器直接通过url获取我们传过去的参数
            特点2: get请求可以直接放在浏览器地址栏测试
            特点3: 项目中一般获取数据,不修改服务器数据使用GET请求

            HTTP协议:
                请求头: GET http://192.168.1.118/teach/gettest/deal.php?username=admin&password=1234 HTTP/1.1

        POST请求
            <form action='deal.php' method='post'>
            </form>
            特点1: 参数不会放在url中, 但是会放在POST请求的请求体中
            特点2:post请求不可以直接放在浏览器地址栏测试, 使用工具或者代码测试接口
                可选的工具是postman
             特点3: 项目中一般需要修改数据,或者上传文件(图片也是文件)使用POST
                上传文件一定要用POST, 一定要加enctype


            HTTP协议
                请求头: POST http://192.168.1.118/teach/posttest/deal.php HTTP/1.1
                请求体: username: admin
                    password: 123

        POST上传文件
            <form action='deal.php' method='post'  enctype="multipart/form-data">
                    <input type="file" name="headImage" />
                </form>
            上传文件一定要用POST, 一定要加enctype="multipart/form-data"



    vue-resource  (vue1.0推荐的网络请求库)
        环境搭建
            如果是普通js, 直接添加脚本 <script src="js/vue/vue-resource.js"></script>
            如果是vue脚手架,
                先install, 在导入, 在Vue.use()

        get
            格式:  this.$http.get(url网址, option选项一般不写)
                            .then(成功回调函数)
                            .catch(失败回调函数)

                    option常用选项
                        headers: 添加请求头


        post
            格式:  this.$http.post(url网址, data附加参数, option选项一般不写)
                            .then(成功回调函数)
                            .catch(失败回调函数)

            特别注意: 默认发生请求头 Content-Type: application/json;charset=UTF-8
                服务器识别不了, 一般都用 Vue.http.options.emulateJSON = true;

        vue-resource文件上传(上传图片文件,预览选择的图片)
            问题1: 如何选择需要的的图片?
                web开发有input type="file",选择文件, 选择图片

            问题2: 选择了图片之后, 在js代码如何获取图片?
                input标签, 有个属性files, 是个数组, 这里面存储所有选择的图片
                得到的是file对象, img中显示图片需要图片的路径
                需要利用 window.URL.createObjectUrl()


            问题3: 在html中通过form表单和submit上传文件, js代码,没有form
                通过创建一个formData对象, 通过这个对象上传


    axios  (vue2.0推荐的网络请求库)
        环境搭建
            如果是普通js, 直接添加脚本 <script src="js/axios/axios.min.js"></script>
            如果是vue脚手架,
                先install, 再导入, 在Vue.use()

        get
            问题: 如何获取到axios对象
            this.$http和axios

        post
            注意: axios.post第二个参数是请求的附加数据, 这个数据传入一般不要使用对象,如果使用对象
                content-type: application/json这种格式, php后台无法处理这种格式

                直接写字符串,格式: username=admin&password=123

        文件上传
            注意: axios中post上传默认, 文件上传需要的content-type: , 需要设置请求头请求类型


        请求拦截(拦截)

            应用功能场景:
                登录之后, 每个请求请求头中需要添加token, 怎么加?
                    笨办法: 一个请求一个请求加
                    好办法: 使用拦截器, 如果有100个请求, 都会走拦截器

                返回响应的有可能token失效了, 告诉用户登录失效了,得重新登录
                    笨办法: 在所有页面所有请求中都检查是否失效, 或者是否版本过期
                    好办法: 使用拦截器, 如果有100个请求, 都会走拦截器


            拦截请求:  格式 axios.interceptors.request.use(config回调函数, 错误处理函数)
                回调函数调用传入config对象, 这是这个请求的配置对象, 里面有所有选项

            拦截响应: 格式 axios.interceptors.response.use(response回调函数, 错误处理函数)
                回调函数传入response对象, 这个对象就是返回的响应对象

            注意: 执行以上的代码, 所有请求和响应都会执行以上的代码


        多个请求
            用的比较少, 简单说一下

    总结:
        问题1: 以后用哪个比较多?
            axios用的多, 推荐一种
            vue-resource新项目不要用了, 维护旧项目可以用

        问题2: vue-resource和axios有什么区别?
            vue-resource是早期的网络请求,vue1.0推荐使用
            特点: <1>体积小
                    <2>支持主流的浏览器
                    <3>支持promise
                    <4>支持拦截器
                    ...
            axios是vue2.0推荐使用的库
            特点: <1>支持主流的浏览器
                    <2>支持promise
                    <3>支持拦截器
                    <4>支持并发请求(多个请求)
                    <5>取消请求
                    <6>支持安全保护....

        问题3: 我学了这个多, 感觉有点少?
            中文文档: https://segmentfault.com/a/1190000008470355
            github: https://github.com/axios/axios

13.路由 vue router

    介绍
        q.路由是干嘛用的?
            路由一般用于vue中界面的切换

        q.普通的界面界面用a标签就能切换, 为什么要用路由?
            实现了单页面应用(SPA单页面应用)

        q.什么是SPA单页面应用?
            单页面应用指的不是只有一个页面的应用, 而是指网站只有一个html文件,所有界面切换都在这个html上实现

        q.为什么使用单页面应用, 好处?
            多个html之间切换, 带啦问题, A html上有个vue实例, 切到B html有个vue实例, A vue实例中数据不会直接传到b vue实例中,
            vue最好是真个项目中只有一个vue实例, 不同的界面都是一个一个组件

        q.单文档应用一般都有什么特性?
            第一个加载html比较慢, 以后比较快, 界面就是组件的切换, 不会下载新的html

            以前的写的代码, 每次显示新的界面, 都要下载一个新的html

        q.参考
            vue-router首页 : https://router.vuejs.org/zh/
            基础案例: https://router.vuejs.org/zh/guide/#html

    基本使用
        <1>加载vue-router.js库文件
        <2>创建多个页面, 其实创建多个组件(一个界面一个组件)
        <3>定义一个路由规则(指定一个路径对应一个界面)
        <4>实例中加载使用路由规则
        <5>view中添加一个router-view, 去显示当前的界面
        <6>切换切换使用router-link, 添加router-link去切换不同的界面


        特征:  界面切换的时候就是一个html, 里面就一个vue实例, 不会创建的新的vue实例
                界面变化的时候, 真正变化的URL的#后面部分, vue检测到这个变化,直接切换显示的组件

        注意的地方:
            router-view替换成对应的组件的template
            router-link 替换成a标签, 添加样式知道是给a添加


    路由传值 ****
        q.普通传值是干嘛呢?什么地方使用它?
            传值是非常常见的技术, 以前html界面和html界面之间传值
                sessionStorage
                通过url   href="b.html?a=10"

        q.路由传值是什么什么,什么作用?
            一个html界面内切换路由去显示不同界面, A界面跳转到B界面, 需要传值的,用路由传值
            例子: 一个列表页显示10个数据, 详情页显示的数据取决于点击了列表页哪个数据
                干的事情, 要点击的数据的id, 传递给详情页

        q.路由传递参数实现的步骤


            前置的功能 - 实现列表页到详情页跳转
                1> 创建了 bookDetail/musicDetail/filmDetail
                2> 在路由规则中添加路由   /bookDetail   不带参数
                3> 在book界面添加链接地址, 跳转到bookDetail

            实现路由传参
            <1>改造路由path, 添加参数  /readDetail  =>    /readDetail/:id
                格式:  /路由路径/:参数名

            <2>路由跳转到的传入参数
                以前  to="/readDetail"   =>  to="/readDetail/100"

            <3>在目标界面上获取传递的参数
                放在  this.$router.params中, 获取this.$router.params.id


    js中路由跳转
        q.以前界面跳转?
            <a href="b.html?a=10">
            <script>
                window.location.href = "b.html?a=10"
            </script>

        q.路由中界面跳转?
            <router-link to="/readDetail"></router-link>
            <script>
                路由对象  push  显示某个路由对应界面
                        replace 替换显示某个界面
                        go 前进或者后退几步
            </script>

    命名路由
        q.什么是命名路由,作用是什么?
            就是给路由起个名字,通过名字访问路由

            比较长的path简化为短的名字, 实现快速访问

        q.如何使用
            定义的时候在每个path下面添加一个name, 对应的值是字符串
                {
                    path:"/main/book/bookDetail/:id",
                    name:"bookDetail"
                }
            然后跳转
                <router-link v-bind:to="{name:'bookDetail',params:{id:100}}"></router-link>
                this.$router.push({
                    name:'bookDetail',
                    params:{id:100}
                })

    路由重定向
        q.路由重定向作用?
            访问一个路由时候想要让这个路由跳转到其他路由


        q.如何使用
            定义路由的时候,不用加组件, 而是添加属性redirect:""
            对应的值是另外一个路径

            案例:
            {
                path: "/book",
                redirect: "/"
            }

    路由导航守卫(路由钩子)

        q.路由导航守卫是干嘛的?
            有的时候, 我要想要在路由显示一个界面的时候,做出控制,例如有些界面登录不让进入
            监控路由, 做出处理


        q.路由钩子有哪些?
            全局路由钩子(常见)
            组件路由钩子(常见)
            路由定时钩子(较少)


        q.全局钩子怎么用
            router定义的下面, 每个路由跳转之前, 执行回调函数
            router.beforeEach((to, from, next)=>{

            })

            router定义的下面, 每个路由跳转之后, 执行回调函数
            router.afterEach((to, from, next)=>{

            })

        q.组件内钩子怎么用
            beforeRouteEnter(to, from, next){
                next()
            }
            beforeRouteUpdate(to, from, next){
                next()
            }
            beforeRouteLeave(to, from, next){
                next()
            }

14.复习总结

    传值1-父传子
        步骤1: 使用组件的地方, 给组件添加属性,属性传入一个值,格式不限
            <goods-count init-count="100"></goods-count>
        步骤2: 给组件添加一个属性props,这个属性对应的是一个数组,里面放都是字符串,每个字符串是一个变量名字,需要注意,后面使用变量, 字符串遵循是变量规则, 最好使用小驼峰式语法
        步骤3: 使用方式1, 在template中通过 {{initCount}}使用
                使用方式2: 在js中通过 this.initCount去使用

        注意1: 传入的属性能直接改吗?
            不能
        注意2: 组件外通过数据绑定修改参数的值, 内部的属性值自动变化

    传值2-子传父
        步骤1:  组件内部通过组件自带的函数 this.$emit(), 发起自定义事件
            格式: this.$emit(自定义事件名, 附加参数多个-可不写)
                this.$emit(eventName, [...args])

        步骤2: 使用组件的地方, 通过  @自定义事件名,  去监听自定义的事件的发生,绑定函数


        步骤3: 使用组件的地方, 在methods中添加处理函数, 添加参数
            注意: 参数可以不加, 加的类型可以是基本类型, 数组, 对象, 函数对象


    传值3-事件总线
        步骤1: 所有组件前,定义一个空的vue实例, 作为事件总线
            注意: 所有组件前?  因为组件内要用实例
            var eventBus = new Vue()

        步骤2: 在第一个界面上发出自定义事件, 具体格式和子传父类似
            格式: this.$emit(自定义事件名, 附加参数多个-可不写)
                eventBus.$emit(eventName, [...args])

        步骤3: 在第二个界面的created中监听事件, 通过$on这个函数
            格式:   this.$on( event, callback )

                eventBus.$on(事件名, 回调函数-最好是箭头 )



    生命周期

    axios

15.实例练习

附件问题

    $问题
        学习顺序: 博客->文档->视频
            实例中的vue自带属性和自带函数之前,vue都加了$,

        避免和你在 data 和 methods 定义的属性和函数冲突

    {}问题
        微信中: 只要是变量, 都需要放在{{}}之中
            wx:if="{{isShow}}" wx:for="{{list}}"

        vue中
            一个标签, 属性进行渲染分两种请求 v-model="data定义的变量"
                <input v-mode="num" v-bind:style="data定义的变量">

            标签内内容, 渲染的时候加上{{}}
                <p> {{num}} </p>

        react
            {} 使用单括号

        angular
            和vue类似

###1.2 简易项目

##2.Vue 脚手架相关(Web 工程化开发)
###2.1 npm
###2.2 vue 脚手架
###2.3 简易项目

###3.Vue 项目
##3.1 svn
##3.2 git
##3.3 一个 Vue 中型项目

##react

##工程化
