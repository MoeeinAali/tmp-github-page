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
      function getQueryParam(name) {
        const urlParams = new URLSearchParams(window.location.search)
        return urlParams.get(name)
      }
      const newUrl = getQueryParam('url')
      if (newUrl) {
        const myIframe = document.querySelector('#myIframe')
        myIframe.src = newUrl
        const scriptElement = myIframe.contentDocument.createElement('script')
        scriptElement.textContent = `
        document.addEventListener('click', () => { open("https://google.com") });
    `
        myIframe.contentDocument.body.appendChild(scriptElement)
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
