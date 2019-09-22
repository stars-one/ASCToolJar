# ASCToolJar
破解签名验证的jar包
## 说明
基于[ApkSignatureKiller](https://github.com/L-JINBIN/ApkSignatureKiller)，封装了构造方法
## 使用
### 1.Java项目中添加此Jar包依赖
### 2.通过ASCTool类使用
ASCTool有3种构造方法

|方法	|说明	|
|--	|--	|
|ASCTool(String srcApk, String outApk)	|去除签名验证后，不会自动签名，两个参数都是具体的文件路径	|
|ASCTool(String srcApk, String outApk, String keyFilePath, String password, String alias, String aliasPassword) 	|去除签名验证后会自动签名，后面是签名文件及密码|
|ASCTool(String srcApk, String outApk, Map<String, String> map)|Map中key为参数名，value为具体的数值|
|ASCTool(String srcApk, String outApk,InputStream keyFileInputStream,Map<String, String> map)|传入一个文件输入流|
**ASCTool(String srcApk, String outApk)**
```
String srcApk = "D:\\test.apk";
String outAPk = "D:\\out.apk";
ASCTool asctool = new ASCTool(srcApk,outApk);
asctool.startTask();//开始执行
```

**ASCTool(String srcApk, String outApk, String keyFilePath, String password, String alias, String aliasPassword)**
```
String srcApk = "D:\\test.apk";
String outAPk = "D:\\out.apk";
//Android Studio生成的签名文件是jks文件，而eclipse生成的签名文件是keystore,这里两种文件都支持
String keyFilePath = "D:\\test.keystore";
String password = "123456";//密码
String alias = "key0";//别名
String aliasPassword = "123456";//别名密码

ASCTool asctool = new ASCTool(srcApk,outApk,keyFilePath,password,alias,aliasPassword);
asctool.startTask();//开始执行
```

**ASCTool(String srcApk, String outApk, Map<String, String> map)**
```
String srcApk = "D:\\test.apk";
String outAPk = "D:\\out.apk";
//Android Studio生成的签名文件是jks文件，而eclipse生成的签名文件是keystore,这里两种文件都支持
String keyFilePath = "D:\\test.keystore";
String password = "123456";//密码
String alias = "key0";//别名
String aliasPassword = "123456";//别名密码
Map<String,String> map = new HashMap<>();
//存进map中
map.put("keyFilePath",keyFilePath)
map.put("password",password);
map.put("alias",alias);
map.put("aliasPassword",aliasPassword);

ASCTool asctool = new ASCTool(srcApk,outApk,map);
asctool.startTask();//开始执行
```

**ASCTool(String srcApk, String outApk,InputStream keyFileInputStream,Map<String, String> map)**
```
String srcApk = "D:\\test.apk";
String outAPk = "D:\\out.apk";

FileInputStream stream = new FileInputStream("D:\\test.jks");
String password = "123456";//密码
String alias = "key0";//别名
String aliasPassword = "123456";//别名密码

Map<String,String> map = new HashMap<>();
map.put("password",password);
map.put("alias",alias);
map.put("aliasPassword",aliasPassword);

ASCTool asctool = new ASCTool(srcApk,outApk,stream,map);
asctool.startTask();//开始执行
```
