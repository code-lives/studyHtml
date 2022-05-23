# js设置div滑动到顶，就固定不动。类似于顶部导航固定

````javascript
var elm = $('.consulting');
var startPos = $(elm).offset().top;
$.event.add(window, "scroll", function() {
    var p = $(window).scrollTop();
    $(elm).css('position', ((p) > startPos) ? 'fixed' : 'static');
    $(elm).css('top', ((p) > startPos) ? '0px' : '');
});
````