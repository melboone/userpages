Bulma Modal 模態窗 的 JavaScript 程式碼
#######################################

:date: 2018-10-15T23:54+08:00
:tags: JavaScript
:category: JavaScript
:summary: Bulma *modal* 模態窗 組件 的 JavaScript 程式碼。
          程式碼是從 Bulma 官方網站擷取而來的。
:og_image: https://www.designil.com/wp-content/uploads/2016/10/modal-box-bulma.png
:adsu: yes


本文是給那些不想自己寫 JavaScript 程式碼，而只想用跟 Bulma_ 官方網站 modal_
模態窗 [1]_ 一樣程式碼的人。

此 JavaScript 程式碼來自官方網站所用的 *main.js* [2]_ 。
我把程式碼放在本文以方便透過谷歌或其他搜尋引擎來搜索。

.. code-block:: javascript

  'use strict';
  
  document.addEventListener('DOMContentLoaded', function () {
  
    // Modals
  
    var rootEl = document.documentElement;
    var $modals = getAll('.modal');
    var $modalButtons = getAll('.modal-button');
    var $modalCloses = getAll('.modal-background, .modal-close, .modal-card-head .delete, .modal-card-foot .button');
  
    if ($modalButtons.length > 0) {
      $modalButtons.forEach(function ($el) {
        $el.addEventListener('click', function () {
          var target = $el.dataset.target;
          var $target = document.getElementById(target);
          rootEl.classList.add('is-clipped');
          $target.classList.add('is-active');
        });
      });
    }
  
    if ($modalCloses.length > 0) {
      $modalCloses.forEach(function ($el) {
        $el.addEventListener('click', function () {
          closeModals();
        });
      });
    }
  
    document.addEventListener('keydown', function (event) {
      var e = event || window.event;
      if (e.keyCode === 27) {
        closeModals();
      }
    });
  
    function closeModals() {
      rootEl.classList.remove('is-clipped');
      $modals.forEach(function ($el) {
        $el.classList.remove('is-active');
      });
    }
  
    // Functions
  
    function getAll(selector) {
      return Array.prototype.slice.call(document.querySelectorAll(selector), 0);
    }
  
  });

**Demo**:

.. raw:: html

  <br>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.6.2/css/bulma.min.css">
  <a class="button is-primary is-large modal-button" data-target="modal-bis">Launch image modal</a>

  <div id="modal-bis" class="modal">
    <div class="modal-background"></div>
    <div class="modal-content">
      <p class="image is-4by3">
        <img src="https://bulma.io/images/placeholders/1280x960.png">
      </p>
    </div>
    <button class="modal-close is-large" aria-label="close"></button>
  </div>

  <br><br>

  <script>
  'use strict';
  
  document.addEventListener('DOMContentLoaded', function () {
  
    // Modals
  
    var rootEl = document.documentElement;
    var $modals = getAll('.modal');
    var $modalButtons = getAll('.modal-button');
    var $modalCloses = getAll('.modal-background, .modal-close, .modal-card-head .delete, .modal-card-foot .button');
  
    if ($modalButtons.length > 0) {
      $modalButtons.forEach(function ($el) {
        $el.addEventListener('click', function () {
          var target = $el.dataset.target;
          var $target = document.getElementById(target);
          rootEl.classList.add('is-clipped');
          $target.classList.add('is-active');
        });
      });
    }
  
    if ($modalCloses.length > 0) {
      $modalCloses.forEach(function ($el) {
        $el.addEventListener('click', function () {
          closeModals();
        });
      });
    }
  
    document.addEventListener('keydown', function (event) {
      var e = event || window.event;
      if (e.keyCode === 27) {
        closeModals();
      }
    });
  
    function closeModals() {
      rootEl.classList.remove('is-clipped');
      $modals.forEach(function ($el) {
        $el.classList.remove('is-active');
      });
    }
  
    // Functions
  
    function getAll(selector) {
      return Array.prototype.slice.call(document.querySelectorAll(selector), 0);
    }
  
  });
  </script>

----

**You might be interested in ...**

- `[Vue.js] Bulma Modal <{filename}/articles/2018/09/27/vuejs-bulma-modal%en.rst>`_
- `Bulma Modal with Pure CSS Toggle <{filename}/articles/2018/01/27/css-only-toggle-bulma-modal%en.rst>`_
- `Bulma Modal with Go Toggle <{filename}/articles/2017/12/04/bulma-modal-with-go-toggle%en.rst>`_

----

Tested on:

- ``Chromium 64.0.3282.140 on Ubuntu 17.10 (64-bit)``
- ``Bulma 0.6.2``

----

.. adsu:: 2

**References**:

.. [1] `Modal | Bulma: a modern CSS framework based on Flexbox <https://bulma.io/documentation/components/modal/>`_
.. [2] `https://bulma.io/lib/main.js?v=201802091742 <https://bulma.io/lib/main.js?v=201802091742>`_

.. _Bulma: https://bulma.io/
.. _modal: https://bulma.io/documentation/components/modal/
