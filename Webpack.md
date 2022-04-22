# css工程化\三
    六,预编译less
        1,css的问题
            (1)重复的代码段:例如清除浮动,绝对定位
            (2)重复样式值:列入常用颜色,常用居中
            (3)重复嵌套书写:列如重复命名前缀
        [扩展]数据网站
            less官网:http://lesscss.org/
            less中文0网站(非官方):http://lesscss.cn/
            less中文1网站(非官方):https://less.bootcss.com/

            sass官网:https://sass-lang.com/
            sass中文0网站(非官方):https://sass.hk/
            sass中文1网站(非官方):https://sass.bootcss.com/
        2,安装
            安装:npm install less -g
            节点安装:npm i less --save-dev
        3,less基本使用
            (1)变量(Variables):常用值的储存

                {
                    @a = 10px

                    .xxx{
                        width:@a == width:10px
                    }
                }
            
            (2)混合(Mixins):css中样式的条件集合,可以以函数形式在其他集合执行

                {
                    .a{
                        color:#fff
                    }

                    .b{
                        .a()
                    }
                    [补充]
                        1,.a(){}可以只提供内部条件,不生成样式
                        2,.a(@xx:默认值){color:@xx}可以用函数的形式进行传值,同样可以提供默认值
                        3,更多详细功能去官网查看
                }

            (3)嵌套(Nesting):css中子集样式放入父集样式中进行嵌套,同集样式平行放入

                {
                    <div class="a">
                    <div class="b"></div>
                    <div class="c"></div>
                    </div>

                    .a{
                        .b{.d}
                        .c{}
                    }
                    [补充]
                        1,支持多种格式
                        2,.a{>::b}等
                        3,.a{b{&.selected}}支持点击事件
                }

            (4)运算(Operations):会将编译数据进行运算,返回结果
              * 注意单位:有些单位不互通,有些单位会进行计算

              {
                  @a = 10px
                  .b{
                      width:@a*2 == 20px
                  }
              }

            (4)函数(Functions):支持函数运算,详细内容看手册
                非官方手册地址:https://less.bootcss.com/functions/#color-definition-functions

            (5)作用域(Scope):在块级区域生效使用,不在全局生效,就近原则向上查找

                {
                    @ff = 20px
                    .a{
                        @ff = 10px
                        height:@a == 10px
                        .b{
                            height:@a == 10px
                        }

                    }
                }

            (5)注释(Comments):新增单行lcss注释,依旧支持css注释
                
                {
                    //lcss注释,多用于单行
                    /*
                    css注释,多用于多行
                    */
                }

            (6)导入(Importing):与css相同,可以直接导入其他编译lcss条件属性进行使用
              *当变量名发生冲突时,优先使用后面声明的变量

                {
                    @import"导入lcss名称";
                }

            (7)映射(Maps):**未理解>>应该为可直接调用其他编译的lcss条件属性

                {
                    #colors(){
                        colors = #fff
                    }
                    .b{
                        colors = #colors[colors]
                    }
                }
                



