## 开发函数库
-----------------

1，移动端兼容IOS、安卓的复制方法 
...
/**
 * @description 移动端兼容IOS、安卓的复制方法
 * @param select 选择器
 * @param text 需要复制的文本
 */

function copy (select, text){
  if (navigator.userAgent.match(/(iPhone|iPod|iPad);?/i)) {//区分iPhone设备
        var copyDOM = document.querySelector(`#${select}`);  //要复制文字的节点
        var range = document.createRange();
        // 选中需要复制的节点
        range.selectNode(copyDOM);
        // 执行选中元素
        window.getSelection().addRange(range);
        // 执行 copy 操作
        var successful = document.execCommand('copy');
        try {
            var msg = successful ? 'successful' : 'unsuccessful';
            console.log('copy is' + msg);
        } catch (err) {
            console.log('Oops, unable to copy');
        }
        // 移除选中的元素
        window.getSelection().removeAllRanges();
        // alert("已复制链接!");
  } else {
        // 创建元素用于复制
        var aux = document.createElement("input");
        // 获取复制内容
        var txt = text;
        // 设置元素内容
        aux.setAttribute("value", txt);
        // 将元素插入页面进行调用
        document.body.appendChild(aux);
        // 复制内容
        aux.select();
        // 将内容复制到剪贴板
        document.execCommand("copy");
        // 删除创建元素
        document.body.removeChild(aux);
        console.log(document.execCommand("copy"));
    }
}

...
