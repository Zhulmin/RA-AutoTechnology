# Auto-technology


### 持续集成 CI
使用 Jenkins 和 [fastlane](https://github.com/fastlane/fastlane) 实现自动化测试打包发布AppStore等平台  
Jenkins 只用于持续集成, Jenkins的xcode插件超级难用  
fastlane 用于自动打包/发布  
  
  
##### fastlane文件实例: 自定义lane 
```
lane :debug do
  gym(
    clean: true,
    export_method: "development",
    scheme: "SwiftProject",
    output_directory: "/Users/rain/Desktop/package",
    configuration: "Debug",
    silent: true,
    export_options: {compileBitcode: false}
    )
end
```
  
##### jenkins执行shell脚本
```
fastlane [lane name] [op]  
```
  
  
  
#### 遇到的的问题  
Jenkins 从github 获取仓库需要配置[token]https://github.com/settings/tokens/new  
Jenkins 需安装 Github plugin 插件  安装路径: 系统管理 >> 系统设置 >> GitHub Plugin Configuration  

  
### 参考资料  
[fastlane文档](https://docs.fastlane.tools/)  
[iOS中fastlane的使用](http://blog.devzeng.com/blog/ios-fastlane-in-action.html)  
[iOS中使用Fastlane实现自动化打包和发布](http://www.cocoachina.com/ios/20170519/19317.html)  
      
  
  
  

### 使用sh脚本打包(舍弃的方法)
* [iOS-AutoPackage](https://github.com/913868456/iOS-AutoPackage) 使用shell脚本打包
  
#### 该方法Xcode 8.3版本过期, Xcode更新以后缺少[PackageApplication](https://pan.baidu.com/s/1i4BErJ3)文件

报错:
```shell
xcrun: error: unable to find utility “PackageApplication”, not a developer tool or in PATH
```
  
解决办法：从老版本拷贝该文件到这个路径 
```shell
/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/usr/bin 
```
  
执行命令:
```shell
sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer/
```
```shell
chmod +x /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/usr/bin/PackageApplication
```
  
  
    
