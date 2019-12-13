<div onload="checkCookie()"></div>

<button onclick="cookie_Agree();">點我清除Cookie</button>



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
    alert("Welcome again " + user);
  } else {
     user = prompt("Please enter your name:","");
     if (user != "" && user != null) {
       setCookie("username", user, 30);
     }
  }
}

function clearAllCookie() {
    ////alert('123');
    //var keys = document.cookie.match(/[^ =;]+(?=\=)/g);
    //if (keys) {
    //    for (var i = keys.length; i--;)
    //    document.cookie = keys[i] + '=0;expires=' + new Date(0).toUTCString()+'; path=/' + domain;
    //}
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
//clearAllCookie();

</script>
