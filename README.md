# QQlogin
第三方qq登录集成

使用
1、第一步
public class myapp extends Myapp {
    {
        {
            PlatformConfig.setQQZone("100424468", "c7394704798a158208a74ab60104f0ba");
        }
    }
    @Override
    public void onCreate() {
        super.onCreate();
        UMShareAPI.get(this);
    }
}

2、第二步

  UMShareAPI.get(MainActivity.this).getPlatformInfo(MainActivity.this, SHARE_MEDIA.QQ, new UMAuthListener() {
                    @Override
                    public void onStart(SHARE_MEDIA share_media) {

                    }

                    @Override
                    public void onComplete(SHARE_MEDIA share_media, int i, Map<String, String> map) {
                        final String name = map.get("name");
                        runOnUiThread(new Runnable() {
                            @Override
                            public void run() {
                                Toast.makeText(MainActivity.this,"当前用户为:"+name,Toast.LENGTH_LONG).show();
                            }
                        });

                        System.out.println("==================================="+name);
                    }

                    @Override
                    public void onError(SHARE_MEDIA share_media, int i, Throwable throwable) {

                    }

                    @Override
                    public void onCancel(SHARE_MEDIA share_media, int i) {

                    }
                });
