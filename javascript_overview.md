# JavaScript Overview

## Global ```index.js```

<!--
https://github.com/pinax/pinax-starter-projects/blob/<project_name>/static/src/js/index.js
-->

```javascript
/* global $ */
import '../scss/index.scss';

import ajaxSendMethod from './ajax';
import handleMessageDismiss from './messages';

require('bootstrap/dist/js/bootstrap.bundle');

$(() => {
  $(document).ajaxSend(ajaxSendMethod);

  // Topbar active tab support
  $('.topbar li').removeClass('active');

  const classList = $('body').attr('class').split(/\s+/);
  $.each(classList, (index, item) => {
    const selector = `ul.nav li#tab_${item}`;
    $(selector).addClass('active');
  });

  $('#account_logout, .account_logout').click((e) => {
    e.preventDefault();
    $('#accountLogOutForm').submit();
  });

  handleMessageDismiss();
});
```

## Global ```ajax.js```

<!--
https://github.com/eldarion/eldarion-ajax
-->

AJAX is used to update a page in real time, without reloading the page.

```javascript
    require('eldarion-ajax');
```

<!--
https://github.com/pinax/pinax-starter-projects/blob/<project_name>/static/src/js/ajax.js
-->

```javascript
/* global document jQuery */
/* eslint no-plusplus: ["error", { "allowForLoopAfterthoughts": true }] */

const getCookie = (name) => {
  let cookieValue = null;
  if (document.cookie && document.cookie !== '') {
    const cookies = document.cookie.split(';');
    for (let i = 0; i < cookies.length; i++) {
      const cookie = jQuery.trim(cookies[i]);
      // Does this cookie string begin with the name we want?
      if (cookie.substring(0, name.length + 1) === `${name}=`) {
        cookieValue = decodeURIComponent(cookie.substring(name.length + 1));
        break;
      }
    }
  }
  return cookieValue;
};

const sameOrigin = (url) => {
  // url could be relative or scheme relative or absolute
  const { location } = document;
  const { host, protocol } = location;
  const srOrigin = `//${host}`;
  const origin = `${protocol}${srOrigin}`;

  // Allow absolute or scheme relative URLs to same origin
  return (url === origin || url.slice(0, origin.length + 1) === `${origin}/`)
      || (url === srOrigin || url.slice(0, srOrigin.length + 1) === `${srOrigin}/`)
      // or any other URL that isn't scheme relative or absolute i.e relative.
      || !(/^(\/\/|http:|https:).*/.test(url));
};

const safeMethod = method => /^(GET|HEAD|OPTIONS|TRACE)$/.test(method);

const ajaxSendMethod = (event, xhr, settings) => {
  if (!safeMethod(settings.type) && sameOrigin(settings.url)) {
    xhr.setRequestHeader('X-CSRFToken', getCookie('csrftoken'));
  }
};

export default ajaxSendMethod;
```

## Global ```messages.js```

<!--
https://github.com/pinax/pinax-starter-projects/blob/<project_name>/static/src/js/messages.js
-->

```javascript
/* global $ */

const handleMessageDismiss = () => {
  $('.message button[data-dismiss="message"]').click((e) => {
    $(e.currentTarget).closest('.message').remove();
  });
};

export default handleMessageDismiss;
```

## Global ```messages.js```

<!--
https://github.com/pinax/pinax-starter-projects/blob/<project_name>/static/src/js/apps/pinax-documents.js
-->

```javascript
/* global $ */
const hookupCustomFileWidget = () => {
  const $el = $('body.pinax-documents .custom-file').find('input[type=file]');
  //   <label class="custom-file">
  //   <input type="file" id="file2" class="custom-file-input">
  //   <span class="custom-file-control"></span>
  // </label>
  $el.change((e) => {
    const { files } = e.currentTarget;
    $el.parent().find('.custom-file-control')
      .attr('data-file', files.length === 1 ? files[0].name : '')
      .attr('data-files', files.length);
  });
};

export default hookupCustomFileWidget;
```
