###Django有關CSRF遇到的問題，以及解法

最近在看Python web相關的framework

原本看的flask，了解到是用在小型專案中

目前正在研究的是Django(v1.10)，有較完整的專案管理，適合用在較大型的專案

=======

然而…最近在使用form時遇到了一個問題

是關於…csrf的部份

由於Django預設是有開啟CSRF攻擊的防護

是在settings.py中MIDDLEWARE_CLASSES的 -> **'django.middleware.csrf.CsrfViewMiddleware'**

網路上查到的資料都是說只要在html中form加入{% csrf_token %}

就可以解決CSRF token missing or incorrect.的問題。

但是…加入後還是無法解決此問題…

因此就直接把csrf的防護先關閉，或是加入忽略的tag

只要引用 from django.views.decorators.csrf import csrf_exempt

而在func前加上@csrf_exempt

就可以忽略掉csrf的檢查…

原本是使用from django.shortcuts import render_to_response

======

最後找到解法

是用使 from django.shortcuts import render

func回傳 => return render(request, "filename.html")

以上的寫法就能得到{% csrf_token %}