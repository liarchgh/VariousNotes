# [Firefox](https://www.mozilla.org/en-US/firefox/)

## [安装](https://www.mozilla.org/zh-CN/firefox/download/thanks/)

## [about:config](about:config)

```
browser.tabs.drawInTitlebar:true
```

## userChrome.css

```
/* 去除顶部标签栏 */
#main-window[tabsintitlebar="true"]:not([extradragspace="true"]) #TabsToolbar {
  opacity: 0;
  pointer-events: none;
}
#main-window:not([tabsintitlebar="true"]) #TabsToolbar {
    visibility: collapse !important;
}
```