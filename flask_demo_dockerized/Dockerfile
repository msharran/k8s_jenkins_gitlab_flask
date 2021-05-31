FROM python:3.9-alpine
WORKDIR /usr/src/app

RUN python3 -m venv .
RUN source bin/activate
COPY requirements.txt ./
RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 4000

CMD ["gunicorn","-w","4","-b","0.0.0.0:4000","hello_world:APP"]
