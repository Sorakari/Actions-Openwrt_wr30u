# Actions-OpenWrt

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

Build OpenWrt using GitHub Actions

[Read the details in my blog (in Chinese) | 中文教程](https://p3terx.com/archives/build-openwrt-with-github-actions.html)

## 分支说明

- [main](https://github.com/lon91ong/Actions-OpenWrt/tree/main), 源于upstream的配置, 改用[lede-17.01源](https://github.com/coolsnowwolf/openwrt/tree/lede-17.01)
- [bypass](https://github.com/lon91ong/Actions-OpenWrt/tree/bypass), 在main的基础上引入[garypang13/openwrt-packages](https://github.com/garypang13/openwrt-packages)源, 其中的Bypass插件确实好用
- [lienol](https://github.com/lon91ong/Actions-OpenWrt/tree/lienol-19.07), [Lienol-19.07源](https://github.com/Lienol/openwrt)+[garypang13/openwrt-packages](https://github.com/garypang13/openwrt-packages)的Bypass

## Lienol分支说明(主题设置别碰, 别碰, 别...)

> ~~暂时放弃这个分支了, Lienol与lede的配置差别还是蛮大的, 用Youku-Yk1测试了几次, 固件其它功能都还好, 就是主题页侧边栏加载总出错, 虽说可以在SSH安装[**yuyangyu755@恩山**](https://www.right.com.cn/forum/thread-4050369-1-1.html)编译的主题包解决, 但是总没有原生编译的舒服。发了[issue](https://github.com/Lienol/openwrt/issues/574)迟迟没有回复, 不折腾了。~~

[搜索同样的主题问题](https://github.com/Lienol/openwrt/search?q=template.lua&type=issues), 看lienol的回复, 似乎是lienol使用的luci版本比较新, 与现有的主题适配有问题!

**经验总结:** 看[`feeds.conf.default`](https://github.com/Lienol/openwrt/blob/19.07/feeds.conf.default)文件中`luci`源中**对应分支**下的`themes`文件夹下有啥装啥, 不能乱装!

恩山论坛[@小鸡过河](https://www.right.com.cn/forum/space-uid-370176.html)的固件比较有特色, 尤其是科学上网插件Bypass(~~不是买火车票那个分流抢票~~), 但是他用的是lede 5.4内核分支, 稳定性不及4.14内核, 对硬件性能要求比较高, 7621基本算是最低要求了...

本分支使用[Lienol稳定分支](https://github.com/Lienol/openwrt), feed添加了[garypang13/openwrt-packages](https://github.com/garypang13/openwrt-packages), 编译出来在斐讯K2(psg1218a, 7620a方案)跑了几天, 表现尚可。

其它做过的适配改动 [garypang13#10](https://github.com/garypang13/openwrt-packages/issues/10)

#### 常用广告屏蔽

[乘风](https://gitee.com/xinggsf/Adblock-Rule/raw/master/rule.txt)**@**[卡饭](https://bbs.kafan.cn/thread-1866845-1-1.html)

[anti-AD](https://cdn.jsdelivr.net/gh/privacy-protection-tools/anti-AD@master/anti-ad-easylist.txt)**@**[Github](https://github.com/privacy-protection-tools/anti-AD)

## Usage

- Click the [Use this template](https://github.com/P3TERX/Actions-OpenWrt/generate) button to create a new repository.
- Generate `.config` files using [Lean's OpenWrt](https://github.com/coolsnowwolf/lede) source code. ( You can change it through environment variables in the workflow file. )
- Push `.config` file to the GitHub repository.
- Select `Build OpenWrt` on the Actions page.
- Click the `Run workflow` button.
- When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.

## Tips

- It may take a long time to create a `.config` file and build the OpenWrt firmware. Thus, before create repository to build your own firmware, you may check out if others have already built it which meet your needs by simply [search `Actions-Openwrt` in GitHub](https://github.com/search?q=Actions-openwrt).
- Add some meta info of your built firmware (such as firmware architecture and installed packages) to your repository introduction, this will save others' time.

## Acknowledgments

- [Microsoft Azure](https://azure.microsoft.com)
- [GitHub Actions](https://github.com/features/actions)
- [OpenWrt](https://github.com/openwrt/openwrt)
- [Lean's OpenWrt](https://github.com/coolsnowwolf/lede)
- [tmate](https://github.com/tmate-io/tmate)
- [mxschmitt/action-tmate](https://github.com/mxschmitt/action-tmate)
- [csexton/debugger-action](https://github.com/csexton/debugger-action)
- [Cowtransfer](https://cowtransfer.com)
- [WeTransfer](https://wetransfer.com/)
- [Mikubill/transfer](https://github.com/Mikubill/transfer)
- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)
- [ActionsRML/delete-workflow-runs](https://github.com/ActionsRML/delete-workflow-runs)
- [dev-drprasad/delete-older-releases](https://github.com/dev-drprasad/delete-older-releases)
- [peter-evans/repository-dispatch](https://github.com/peter-evans/repository-dispatch)

## License

[MIT](https://github.com/P3TERX/Actions-OpenWrt/blob/main/LICENSE) © P3TERX
