# unity问题集合 #
## 如何动态操作.mat/.fbx文件 ##
.mat文件不能像组件或者预制体一样使用getComponent  
	关键函数：  
AssetImporter.GetAtPath(assetPath) 获取asset，返回值需要强转为对应的importer  

SerializedObject
	序列化一个类  
  	
SerializedProperty rootNodeProperty = modelImporterObj.FindProperty
序列化的importer可以findproperty  


链接：http://www.cnblogs.com/hont/p/4898650.html

## AssetBundle的打包和调用 ##
Assetbundle是可以同时放在服务器或者本地的，无论放在哪里两种下载读取的方式是完全一样的。.U3D和.assetbundle格式都是可能被打成的包。  
可以把prefab或者场景打包等等  
最核心的方法其实就它：
    
    BuildPipeline.BuildAssetBundle (obj, null, targetPath, BuildAssetBundleOptions.CollectDependencies)

参数1：它只能放一个对象，因为我们这里是分别打包，所以通过循环将每个对象分别放在了这里。

参数2：可以放入一个数组对象。

默认情况下打的包只能在电脑上用，如果要在手机上用就要添加一个参数。

Android上：

    BuildPipeline.BuildAssetBundle (obj, null, targetPath,
    BuildAssetBundleOptions.CollectDependencies,BuildTarget.Android)

IOS上:


    BuildPipeline.BuildAssetBundle (obj, null, targetPath, BuildAssetBundleOptions.CollectDependencies,BuildTarget.iPhone)

另外，电脑上和手机上打出来的Assetbundle不能混用，不同平台只能用自己的。

下载Assetbundle使用www类  
`WWW bundle = new WWW(path);`   
本地的读取使用  

    AssetBundle.CreatFromFile

详细参见http://www.xuanyusong.com/archives/2405