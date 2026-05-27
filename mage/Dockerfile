FROM mageai/mageai:latest

WORKDIR /home/src

RUN pip install --no-cache-dir uv

COPY requirements.txt .
RUN uv pip install --system -r requirements.txt || true

EXPOSE 6789

CMD ["mage", "start", "my_project"]
