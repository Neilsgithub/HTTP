
HTTP
=============================================================
 ![](http://www.apkbus.com/data/attachment/forum/201508/26/162351nes8eqe83hhhbple.jpg)
 
 this is a frame for web,You can easily by using the method of inside access to  the network,
 it is Fast and efficient,also save time.the frame based on the okhttp link 
 {https://github.com/square/okhttp} and glide link {https://github.com/bumptech/glide}
 
 How do I use HTTP ?
======================================================================
 
(1) How to use GET obtain String or Object
-------------------------------------------------------------
 ```java
 /**
 * get 中的两个参数 一个url,一个回调监听 监听中可以重写
 * onSuccess(String result)【回调成功】， onError(Exception e)【回调失败】 
 *onStringResult(Stringresult)【打印string】
 */
 Http.get("https://www.baidu.com/", new CallbackListener<String>() {
         @Override
         public void onSuccess(String result) {
                Log.i("cjj", "onSuccess---" + result);
                tv_get_string.setText("getString------->" + result);
            }
 });
 
  Http.get("http://apis.baidu.com/apistore/weatherservice/weather", new CallbackListener<Weather>() {
            @Override
            public void onSuccess(Weather result) {
                super.onSuccess(result);
                Log.i("cjj", "onSuccess---" + result);
                tv_get_object.setText("getObject------->"+result.errMsg +"------"+result.errNum);
            }
            @Override
            public void onError(Exception e) {
                super.onError(e);
                tv_get_object.setText("error:" + e);
            }

            @Override
            public void onStringResult(String result) {
                super.onStringResult(result);
                /**
                 * 一般用于打印String,调试。。。
                 * 如上我们已经知道返回Weather，如果不知道对象是什么，可以先打印出String,就知道对象是怎样的。。。
                 */
            }
        });
        
     /**
     * get 请求
     * @param url
     * @param listener
     */
    public static void get(String url,CallbackListener<?> listener)
    {
        getInstance().baseGet(url, listener);
    }
 ```
 
(2)How to use POST obtain String or Object
--------------------------------------------------------------------------------------------------
```java
 Map<String, String> map = new HashMap<>();
 map.put("key", "7c0fca271915eee1061ab9410352fc26");
 map.put("postcode", "215001");
 Http.post("http://v.juhe.cn/postcode/query", map, new CallbackListener<String>() { //这里直接返回String,也可以返回对象，用法和get的一样，就是post有个参数而已
            @Override
            public void onSuccess(String result) {
                Log.i("cjj", "onSuccess---" + result);
                tv_get_string.setText("getString------->" + result);
            }
 });
 
    /**
     * post 请求
     * @param url
     * @param params
     * @param listener
     */
    public static void post(String url,Map<String,String>params,CallbackListener<?> listener)
    {
        getInstance().basePost(url, params, listener);
    }
 ```
 

 
