---
layout: post
title: Определить текущий media-breakpoint Bootstrap 4 в JavaScript
tags: bootstrap 4, javascript
comments: true
---

Отпуск подошел к концу, а значит нужно сделать пост, дальше времени будет существенно меньше. При изменении нашего сайта agbis.ru мне на паре страниц нужно было проводить несколько операций на маленьком экране. Пошуршав немного на stackoverflow нашел и доработал одно решение. На страницу добавляется невидимый блок, внутри которого несколько блоков на каждый размер. По видимости внутреннего блока определяется, какой сейчас размер. Вдруг кому-то пригодится. Само собой, даже когда внутренний блок становится видимым, то он всё равно скрыт за общим невидимым блоком.

```
<span id="mq-detector" class="invisible">
    <span id="size-xs" class="d-none d-sm-block"></span>
    <span id="size-sm" class="d-sm-none d-md-block"></span>
    <span id="size-md" class="d-md-none d-lg-block"></span>
    <span id="size-lg" class="d-lg-none d-xl-block"></span>
    <span id="size-xl" class="d-xl-none"></span>
</span>
```

```
<script>
    $(function() {
    var currSize = undefined;

    var mqDetector = $("#mq-detector");

    var mqSelectors = [
        mqDetector.find(".d-none"),
        mqDetector.find(".d-sm-none"),
        mqDetector.find(".d-md-none"),
        mqDetector.find(".d-lg-none"),
        mqDetector.find(".d-xl-none")
    ];

    var checkForResize = function() {
        for (var i = 0; i <= mqSelectors.length; i++) {
            if (!mqSelectors[i].is(":visible")) {
            currSize = mqSelectors[i < 1 ? 0 : i-1].attr("id");            
            break;              
            }
        }
    };

    $(window).on('resize', checkForResize);

    checkForResize();

    if (currSize == 'size-xs') {
        //Do something good on XS size
    } 
    
</script>
```

Оформил это в [gist](https://gist.github.com/ToLive/39364b53567e3c46246746c8dabc67e9), чтобы самому не забыть :).