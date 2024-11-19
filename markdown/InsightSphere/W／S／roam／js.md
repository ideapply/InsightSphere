- > js插件主题页，作为尚未收录到`Roam Depot`的本知识库用到的js插件的汇总。
- {{[[DONE]]}} **[Style Roam](https://github.com/JimmyLv/styled-roam)** `#吕立青`
    - {{[[roam/js]]}}
        - ```javascript
          window.URLScriptServer = `https://styled-roam.vercel.app/`
          window.styledRoamDisabledFeatures = [
             'CardListMode',
             'CardFlowMode',
             'TreeTableMode',
             'DocumentMode',
             /*'CalendarMode',*/
             /*'DownloadMode',*/
             /*'FocusMode',*/
          ]
          
          var existing = document.getElementById('styled-roam')
          if (!existing) {
            var extension = document.createElement('script')
            extension.src = window.URLScriptServer + 'js/index.js'
            extension.id = 'styled-roam'
            extension.async = true
            extension.type = 'text/javascript'
            document.getElementsByTagName('head')[0].appendChild(extension)
          }
          ```
