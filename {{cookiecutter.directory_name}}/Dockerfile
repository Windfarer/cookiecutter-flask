FROM python:3.6

ENV TZ 'Asia/Shanghai'

WORKDIR /app

RUN pip install gunicorn gevent
ADD requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt -i https://pypi.douban.com/simple/
COPY . /app

EXPOSE 5000

CMD ["gunicorn", "-k", "gevent", \
     "--max-requests", "3000", \
     "--access-logfile", "-", \
     "--error-logfile", "-", \
     "-b","0.0.0.0:5000", \
     "app:app"]
