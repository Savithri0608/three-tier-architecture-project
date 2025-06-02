FROM python:3.9

ENV HOST="http://localhost:8080/" \
    SILENT=0 \
    NUM_CLIENTS=1 \
    ERROR=0 \
    RUN_TIME=0

WORKDIR /load

COPY requirements.txt /load/

RUN pip install --no-cache-dir -r requirements.txt

COPY entrypoint.sh robot-shop.py /load/

RUN chmod +x entrypoint.sh

CMD ["./entrypoint.sh"]
