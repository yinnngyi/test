<div id="cookieBox">
  <p>為提升本網站的服務品質，本網站透過使用Cookies記錄及存取您的資訊，您可以點擊「拒絕」按鈕，選擇拒絕使用 Cookies 的設置，但可能會無法使用部份本網站個人化服務及部分功能。更多相關資訊請參閱<a href="/www" target="_blank">Cookies聲明</a>。</p>


  <button onclick="cookie_Agree();event.preventDefault();">同意</button>
  <button onclick="cookie_Disagree();event.preventDefault()">不同意</button>
</div>
<button onclick="clearAllCookie();">點我清除Cookie</button>



<script>
function setCookie(cname,cvalue,exdays) {
  var d = new Date();
  d.setTime(d.getTime() + (exdays*24*60*60*1000));
  var expires = "expires=" + d.toGMTString();
  document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
}

function getCookie(cname) {
  var name = cname + "=";
  var decodedCookie = decodeURIComponent(document.cookie);
  var ca = decodedCookie.split(';');
  for(var i = 0; i < ca.length; i++) {
    var c = ca[i];
    while (c.charAt(0) == ' ') {
      c = c.substring(1);
    }
    if (c.indexOf(name) == 0) {
      return c.substring(name.length, c.length);
    }
  }
  return "";
}

function checkCookie() {
  var user=getCookie("username");
  if (user != "") {
  console.log('來過');
      document.querySelectorAll("#cookieBox").style.display = 'none';
  } else {
      console.log('第一次來');
     document.querySelectorAll("#cookieBox").style.display = 'block';
     user = prompt("Please enter your name:","");
     if (user != "" && user != null) {
       setCookie("username", user, 30);
     }
  }
}







function clearAllCookie() {
    document.cookie.split(";").forEach(function (c) { document.cookie = c.replace(/^ +/, "").replace(/=.*/, "=;expires=" + new Date().toUTCString() + ";path=/"); });
    var cookies = document.cookie.split(";");
    var domain = '.' + location.host;
    var TSDomain ='.transcend-info.com';
    console.log(cookies);
    for (var i = 0; i < cookies.length; i++) {
        var cookie = cookies[i];
        var eqPos = cookie.indexOf("=");
        var name = eqPos > -1 ? cookie.substr(0, eqPos) : cookie;
        document.cookie = name + "=;expires=" + new Date().toUTCString() + "; domain=" + domain + "; path=/";
        document.cookie = name + "=;expires=" + new Date().toUTCString() + "; domain=" + TSDomain + "; path=/";
    }
    if (cookies.length > 0) {
        
        console.log(cookies);
        for (var i = 0; i < cookies.length; i++) {
            var cookie = cookies[i];
            var eqPos = cookie.indexOf("=");
            var name = eqPos > -1 ? cookie.substr(0, eqPos) : cookie;
            document.cookie = name + "=;expires=" + new Date().toUTCString() + "; domain=" + domain + "; path=/";
            document.cookie = name + "=;expires=" + new Date().toUTCString() + "; domain=" + TSDomain + "; path=/";
        }
    }

    

}

checkCookie();

</script>
