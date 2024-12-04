url:
```
https://moeeinaali.github.io/tmp-github-page/iranjib/?ad=<Tasvir-URL>&landing=<Landing-url>
```

use this code for all demo templates:
```html
<iframe
      src=""
      frameborder="0"
      id="myIframe"
      scrolling="no"
      style="
        border: 0px solid red;
        width: 100%;
        margin: 0;
        padding: 0;
        position: fixed;
        left: 0;
        right: 0;
        bottom: 0;
        height: 100%;
        max-height: 120px;
      "
    >
    </iframe>

    <script>
      const myIframe = document.querySelector('#myIframe')

      function getQueryParam(name) {
        const urlParams = new URLSearchParams(window.location.search)
        return urlParams.get(name)
      }

      let newUrl = getQueryParam('ad')
      const click_url = getQueryParam('click_url') || 'https://google.com'

      if (click_url) {
        newUrl += `?click_url=${click_url}`
      }

      if (newUrl) {
        myIframe.src = newUrl
      }
    </script>

    <script>
      function handleScroll(e) {
        const scrolled =
          ((document.documentElement.scrollTop || document.body.scrollTop) /
            ((document.documentElement.scrollHeight ||
              document.body.scrollHeight) -
              document.documentElement.clientHeight)) *
          100
        const scrolledInPx =
          document.documentElement.scrollTop || document.body.scrollTop
        const heightOfPage = parent.document.body.scrollHeight
        const myIframe = document.querySelector('#myIframe')
        myIframe.contentWindow.postMessage(
          {
            type: 'yn-window-scroll',
            scrolled,
            scrolledInPx,
            heightOfPage
          },
          '*'
        )
      }

      window.addEventListener('scroll', handleScroll)
    </script>
```
