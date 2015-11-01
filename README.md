##Array posting supported python poster

This repository is forked on https://bitbucket.org/chrisatlee/poster (sha:97d3c6f).
You can post an array like this:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
from poster.encode import multipart_encode
from poster.streaminghttp import register_openers
import urllib2
def post(post_data):
    register_openers()
    datagen, headers = multipart_encode(post_data)
    request = urllib2.Request("http://127.0.0.1/test.php", datagen, headers)
    print urllib2.urlopen(request).read()

if __name__ == '__main__':
    post_data = {
        "array[]":["test1", "test2", "test3", "test4"],
        "uploadFile": open("test.jpg", "rb"),
    }
    post(post_data)
```
```
$ python test.py
Array
(
    [array] => Array
        (
            [0] => test1
            [1] => test2
            [2] => test3
            [3] => test4
        )

)
Array
(
    [uploadFile] => Array
        (
            [name] => test.jpg
            [type] => image/jpeg
            [tmp_name] => /private/var/tmp/php9KAeYD
            [error] => 0
            [size] => 222326
        )

)
Array
(
)
$
```
