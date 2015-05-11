# compute-words
文本框字数统计
例子见[DEMO](http://www.lovewebgames.com/jsmodule/word-count.html)  
![预览效果:](http://www.lovewebgames.com/jsmodule/images/ui/word-count.png "点击预览效果")
#使用方法案例:
    <div class="txt-count-container">
        <div class="counter"><em>30</em></div>
        <textarea name="txt" id="txt" cols="30" rows="10" class="txt">万色城是一个创业平台，所有万色城的网商通过加盟，注册一个属于自己的网上商城。推广自己的商城，销售商城的商品创造收益。每个网商拥有一个属于自己的独立域名。万色城是国内唯一全部实行“实名制”的网上商城，每一个网商，以自己真实的姓名、照片和信誉，作为诚信经营的保障。</textarea>
    </div>
        <p><input type="button" value="点击提交" class="click"></p>
        <script type="text/javascript" src="../src/zepto.js"></script>
        <script type="text/javascript" src="../src/word-count.js"></script>
        <script>
            $(function() {
                $(".click").click(function(){
                    if(!$('.txt').data('overflow') ){
                        alert('ok')
                    }
                });
                $('.txt').WordCount({
                    max:200,
                    isOverflowCut: false,
                    overClass:"over-number",
                    num:$(" .counter em"),
                    withButton:".click",
                    minHeight:100,
                    overflowCallback: function() {
                        //this.textBox.addClass('over-number');
                        //$(".counter em").addClass('over-number');
                    },
                    changeCallback: function(num) {
                        //var n = this.max - num;
                        //$(" .counter em").html(n);
                    },
                    passClallback: function() {
                        //this.textBox.removeClass('over-number');
                        //$(".counter em").removeClass('over-number');
                    },
                    isByte: true//字节
                });
            });
        </script>
#或者:
    var wc = new WordCount();
    wc .init({
            trigger:$('.txt'),
            max:200,
            isOverflowCut: false,
            overClass:"over-number",
            num:$(" .counter em"),
            withButton:".click",
            minHeight:100,
            overflowCallback: function() {
                //this.textBox.addClass('over-number');
                //$(".counter em").addClass('over-number');
            },
            changeCallback: function(num) {
                //var n = this.max - num;
                //$(" .counter em").html(n);
            },
            passClallback: function() {
                //this.textBox.removeClass('over-number');
                //$(".counter em").removeClass('over-number');
            },
            isByte: true//字节
        });
#属性和方法
##trigger  :string || object
    触发的文本框
##max  :number
    最大长度,如果不传会去取文本框的maxlength
##isOverflowCut  :boollen
    是否自动截取文本
##overClass     :string
    超出文本时的样式,会同时在num上和textbox上添加
##num   :element
    显示计数的结点
##minHeight:    number
    文本框的最小高度，因为这里做自适应高度的控制。如没有此参数时，不自适应高度。
##withButton:   element
    关联按钮
##isByte:   boollen
    是否按字节数来计算，true时：一个汉字作2个单位长度，false时汉字英文不作区分
#方法回调:
##overflowCallback:function(n,textbox,max)
    超出时的回调，this指向当前对象,n为长度,textbox是文本框结点对象,max为最大长度
##changeCallback:function(n,textbox,max)
    长度改变时的回调,n为长度,textbox是文本框结点对象,max为最大长度
##passClallback:function(n,textbox,max)
    长度通过时的回调,n为长度,textbox是文本框结点对象,max为最大长度
