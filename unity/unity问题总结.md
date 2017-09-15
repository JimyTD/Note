## unity问题集合 ##
1. ## 如何动态操作.mat文件 ##      
.mat文件不能像组件或者预制体一样使用getComponent  
	关键函数：  
AssetImporter.GetAtPath(assetPath) 获取asset，返回值需要强转为对应的importer  

SerializedObject
	序列化一个类  
  	
SerializedProperty rootNodeProperty = modelImporterObj.FindProperty
序列化的importer可以findproperty  


链接：http://www.cnblogs.com/hont/p/4898650.html