# Firefox

## [安装](https://www.mozilla.org/zh-CN/firefox/download/thanks/)

## [about:config](about:config)

```text
// 顶部显示激活标签的标题
browser.tabs.drawInTitlebar;false
// 双击标签关闭
browser.tabs.closeTabByDblclick;true
// 关闭最后一个标签页不关闭firefox
browser.tabs.closeWindowWithLastTab;false
```

## [userChrome.css](https://www.userchrome.org/)

[一个简易的修改插件](https://addons.mozilla.org/en-US/firefox/addon/fxui-editor/) [一些现成的](https://github.com/andreicristianpetcu/UserChrome-Tweaks)

```text
/* 去除顶部标签栏 */
#main-window[tabsintitlebar="true"]:not([extradragspace="true"]) #TabsToolbar {
  opacity: 0;
  pointer-events: none;
}
#main-window:not([tabsintitlebar="true"]) #TabsToolbar {
    visibility: collapse !important;
}
```

