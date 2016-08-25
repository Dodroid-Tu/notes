###關於Django登入流程的小小理解

最近看了django內建的登入流程

所以今天就來記錄一下登入流程的部份

===

from django.contrib.auth.views import login

上面是Django內建登入的入口

然後真正在驗證帳密的是在django.contrib.auth.forms.py

這是auth中所用到的模板，裡面判斷了資料格式，以及網頁中錯誤提示的部份

在forms.py中取得user object

驗證完使用者的帳密後，下一步就是建立session object

該流程是在django.contrib.auth.__init__.py中的login

該func中檢查了session的相關資訊

最後，就是把session id傳回client端，目前看來是存放在cookie中。