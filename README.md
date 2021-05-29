# CameraManager
Android快速获取相机图片
# 一、前言

应用场景：设备需要定时拍照并上传至服务器、直接获取照片等

# 二、效果图

![效果图](https://upload-images.jianshu.io/upload_images/20395467-d46f061b96fbdd89.gif?imageMogr2/auto-orient/strip)

# 三、如何使用

#### （一）添加库
```
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```
```
	dependencies {
	        implementation 'com.github.Giftedcat:CameraManager:1.0.1'
	}
```

#### （二）初始化
```
        manager = new CameraTakeManager(this)
                .setRotation(0)//设置旋转角度
                .setCompressEnable(true)//是否需要压缩
                .setTakeListener(new CameraTakeListener() {
                    @Override
                    public void onSuccess(File bitmapFile, Bitmap mBitmap) {
                        imgPic.setImageBitmap(mBitmap);
                        tvPicDir.setText("图片路径：" + bitmapFile.getPath());
                    }

                    @Override
                    public void onFail(String error) {
                        LogUtil.e(error);
                    }
                }).launch();
```

#### （三）拍照
```
manager.takePhoto();
```
#### （四）释放
```
manager.destroy();
```
