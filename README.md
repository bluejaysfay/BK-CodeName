javascript:(function() {
  var box = document.createElement('div');
  box.style.position = 'fixed';
  box.style.top = '50%';
  box.style.left = '50%';
  box.style.transform = 'translate(-50%, -50%)';
  box.style.width = '200px';
  box.style.height = '200px';
  box.style.backgroundColor = 'white';
  box.style.border = '2px solid black';
  box.style.zIndex = '9999';
  box.style.cursor = 'move';

  var isDragging = false;
  var offsetX = 0;
  var offsetY = 0;

  box.addEventListener('mousedown', function(e) {
    isDragging = true;
    offsetX = e.clientX - box.getBoundingClientRect().left;
    offsetY = e.clientY - box.getBoundingClientRect().top;
  });

  box.addEventListener('mouseup', function() {
    isDragging = false;
  });

  box.addEventListener('mousemove', function(e) {
    if (isDragging) {
      box.style.top = e.clientY - offsetY + 'px';
      box.style.left = e.clientX - offsetX + 'px';
    }
  });

  document.body.appendChild(box);
})();
