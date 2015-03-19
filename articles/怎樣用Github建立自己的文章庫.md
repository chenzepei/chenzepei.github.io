#用Github建立自己的文章庫  

##項目目标  
多快好省（免費，永不倒閉，方便上傳和修改，有歷史記錄）的個人網絡文章庫存方式。  

##所需技術
1. Github [官網鏈接](https://github.com/)
2. Markdown [簡單入門](http://learnxinyminutes.com/docs/zh-cn/markdown-cn/)
3. strapdownjs [官網連接](http://strapdownjs.com/)

##實現步驟
###申請Github帳號
Just do it.

###新建Repository
Repository name 一定是 {UserName}.github.io，不知道我說什麼的，看一下我的[Github](https://github.com/chenzepei/chenzepei.github.io)。這樣做之後，你就有了一個個人網站啦！雖然什麼都沒有，但是你可以寫啊。馬上上傳一個index.html爽一下先啦。

###使用Strapdownjs來顯示Markdown
我先說一下我對這個網站的構思。很久很久以前，大家的靜態網站是用Html做的，
現在如果還用Html會容易被人笑。而事實我又不需要那些神奇的功能，那是JS的特技，是特技的JS。
Duang的一下，用Markdown來做網站吧。

###廢話不多說，直接上代碼
1. **index.html**
網站的入口，用來跳轉主頁地址到想要的index.md。注意，這個才是我們網站的真正入口，下面的代碼
說的是跳轉到article.html?articles/index.md，article.html是用來把後面的articles/index.md潤色的。
```html
<!DOCTYPE html>
<html>
<script language="javascript">
    window.location.href ="article.html?articles/index.md"
</script>
</html>
```
2. **article.html**
潤色文件，有幾個主題可以用，當然自己寫也是不錯的，這裡使用了cyborg。
至於script裡面的js文件如果你不喜歡多餘的感覺，那麼就直接用鏈接
http://strapdownjs.com/v/0.2/strapdown.js 來代替。
```html
<!DOCTYPE html>
<html>
<xmp id="my_content" theme="cyborg" style="display:none;">
</xmp>
<script type="text/javascript">
  var req = new XMLHttpRequest();
  req.onload = function() {
    var xmpNode = document.getElementById('my_content');
    xmpNode.appendChild(document.createTextNode(this.responseText));
  }
  var url = location.search.substr(1);
  req.open('GET', url, false);
  req.send();
</script>
<script src="strapdown/v/0.2/strapdown.js"></script>
</html>
```
最後你還需要自己寫一個markdown文件作為網站的入口，index.md，就是一個類似於封面的東西。
裡面用來寫連接到其他文章的地址。(如果你不知道該怎麼寫，你還是看回去它的簡單入門吧)

##結束語
本人嘗試過很多方式來保存文章，比如自己開博客(費錢)，用簡書(別人的平台)，
保存在Evernote(總感覺遲早會倒閉的樣子)，之所以最後用這種方式保存自己的文章，
無非覺得這樣簡單，安全。不過這個沒有加密，所以如果是隱私的文件就千萬不要放上去哦。
*題外話 隱私的東西千萬不要聯網，不然什麼都保護不了你。*
