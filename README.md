# IE8
Some compatibility problems for IE8
IE8的一些event事件(IE8及之前通过window.event获得)
  1.有一些事件，比如点击链接或提交表单，会把用户导向另一个页面。为了阻止这类元素的这种默认行为，比如在用户点击链接或提交表单之后还是停留在当前页面，而不是导向新的页面，可以使用事件对象e的preventDefault()。
  IE5~IE8有一个同样功能的属性returnValue，如果将其设置为false，就能达到同样的效果。
  if (e.preventDefault()) {
    e.preventDefault();
  }
  else{
    e.returnvalue = false;
  }

  2.处理完某个元素上的事件之后，可能需要阻止这个事件向其祖先元素继续冒泡传播。这时候，可以使用e.stopPropagation()方法。
  IE8或更早的IE版本中，使用拥有同样功能的属性e.cancelBubble，将其设置为true可以达到同样的效果。
  if (e.stopPropagation) {
    e.stopPropagation();
  }
  else{
    e.cancelBubble = true;
  }

  3.如果你想要同时实现，preventDefault和stopPropagation，可以使用return false。

  $("#a").click(function() {
    $("body").append($(this).attr("href"));
    return false;
  })

  4.event.target事件目标在IE8及之前用event.srcElement
  var target = event.target || event.srcElement;
