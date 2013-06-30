# 腾讯微博SDK for Python

参考 @michaelliao 的 [sinaweibopy](https://github.com/michaelliao/sinaweibopy) 写了个腾讯的API。采用相同的动态 [_http_call()](https://github.com/upbit/tweibo-pysdk/blob/master/tweibo.py#L90) 调用方式，具有代码量少易于维护等特点。

API的详细使用方法见[demo.py](https://github.com/upbit/tweibo-pysdk/blob/master/demo.py)，已测试版本：Python 2.7

## FAQ
1. [OAuth2Handler(): OAuth2鉴权说明](https://github.com/upbit/tweibo-pysdk/wiki/OAuth2Handler)
2. [demo.py详解](https://github.com/upbit/tweibo-pysdk/wiki/demo.py%E8%AF%A6%E8%A7%A3)

***
demo.py演示: 上传example.png并发表微博

```python
    # UPLOAD /t/upload_pic
    pic1 = api.upload.t__upload_pic(format="json", pic_type=2, pic=open(IMG_EXAMPLE, "rb"))
    print ">> IMG: %s" % (pic1.data.imgurl)

    # POST /t/add_pic_url
    content_str2 = "[from PySDK] add pic demo: %s, time %s" % (IMG_EXAMPLE, time.time())
    pic_urls = "%s" % (pic1.data.imgurl)
    tweet_pic1 = api.post.t__add_pic_url(format="json", content=content_str2, pic_url=pic_urls, clientip="10.0.0.1")
    print ">> time=%s, http://t.qq.com/p/t/%s" % (tweet_pic1.data.time, tweet_pic1.data.id)
```

![demo.py运行效果](https://raw.github.com/wiki/upbit/tweibo-pysdk/images/demo.jpg)
