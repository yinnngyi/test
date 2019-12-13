## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/nini-li/works/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/nini-li/works/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.


  
<form>
  Cookie Name: <input name="cName" type="text" /> 
  Cookie Value: <input name="cValue" type="text" />
  <input onclick="doCookieSetup(this.form.cName.value, this.form.cValue.value)"
  type="button" value="設定" />
</form>
<form>
  Cookie Name: <input name="cName" type="text" /> 
  Cookie Value: <input name="cValue" type="text" />
  <input onclick="this.form.cValue.value=getCookie(this.form.cName.value)"
  type="button" value="查詢" />
</form>
<form>
  Cookie Name: <input name="cName" type="text" />
  <input onclick="delCookie(this.form.cName.value)" type="button" value="移除" />
</form>






<script>


//設定 Set cookie
function doCookieSetup(name, value) {
  console.log('123');
  var expires = new Date();
  //有效時間保存 2 天 2*24*60*60*1000
  expires.setTime(expires.getTime() + 172800000);
  document.cookie = name + "=" + escape(value) + ";expires=" + expires.toGMTString()
    console.log('OK');
};
//查詢 Get cookie by name
function getCookie(name) {
  var arg = escape(name) + "=";
  var nameLen = arg.length;
  var cookieLen = document.cookie.length;
  var i = 0;
  while (i & lt; cookieLen) {
    var j = i + nameLen;
    if (document.cookie.substring(i, j) == arg) return getCookieValueByIndex(j);
    i = document.cookie.indexOf(" ", i) + 1;
    if (i == 0) break;
  };
  return null;
};

function getCookieValueByIndex(startIndex) {
  var endIndex = document.cookie.indexOf(";", startIndex);
  if (endIndex == -1) endIndex = document.cookie.length;
  return unescape(document.cookie.substring(startIndex, endIndex));
};

//刪除 Delete cookie entry
function delCookie(name) {
  var exp = new Date();
  exp.setTime(exp.getTime() - 1);
  var cval = getCookie(name);
  document.cookie = escape(name) + "=" + cval + "; expires=" + exp.toGMTString();
};
function listCookie() {
  document.writeln("<table>");
  document.writeln("<tr><th>Name<th>Value");
  cookieArray = document.cookie.split(";");
  for (var i = 0; i < cookieArray.length; i++) {
    thisCookie = cookieArray[i].split("=");
    cName = unescape(thisCookie[0]);
    cValue = unescape(thisCookie[1]);
    document.writeln("<tr><td>" + cName + "</td><td>" + cValue + "</td>");
  };
  document.writeln("</table>");
};

listCookie();

</script>
