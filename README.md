# prac-django

1. docker build -t mysite-sample:1.0 .
2. docker run --rm -it -p 8000:8000 -v ~/PycharmProjects/mysite-sample/:/root/mysite --name mysite-sample mysite-sample:1.0 /bin/bash
