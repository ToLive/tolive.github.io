---
layout: post
title: jQuery и спагетти
tags: javascript
comments: true
---

Знаю, что многие сейчас прилагают усилия, чтобы убрать у себя jQuery из проекта и писать на ванильном javascript. Я пока это не сильно понимаю и разделяю, с учетом размера 3-й версии в 30 кб.
Вот что меня заботит в jQuery, так это стоит ли опасаться спагетти кода, который очень хочется писать? То есть хорошо ли так:  
``` 
$('#submit_order_btn').addClass('btn-secondary').removeClass('btn-primary');
```

Или все же лучше приучить себя к такому:
``` 
let submitOrderBtn = $('#submit_order_btn');

submitOrderBtn.addClass('btn-secondary');
submitOrderBtn.removeClass('btn-primary');
```

Первый вроде короче, но представляет из себя чудовище, когда последовательно идет много операций.