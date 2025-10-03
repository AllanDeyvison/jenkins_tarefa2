# FROM python:3.9-slim

# WORKDIR /app

# COPY requirements.txt .
# RUN pip install --no-cache-dir -r requirements.txt

# COPY app.py .
# COPY test_app.py .
# COPY nginx.conf /etc/nginx/nginx.conf
# COPY index.html /usr/share/nginx/html/

# RUN apt-get update && apt-get install -y nginx && rm -rf /var/lib/apt/lists/*

# EXPOSE 80 5000

# CMD service nginx start && python app.py

FROM python:3.9-slim

# Instala dependências e nginx
RUN apt-get update && \
    apt-get install -y nginx && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Copia e instala dependências Python
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copia arquivos da aplicação
COPY app.py .
COPY test_app.py .

# Copia configurações do nginx e index.html
COPY nginx.conf /etc/nginx/nginx.conf
COPY index.html /usr/share/nginx/html/index.html

# Expõe portas necessárias
EXPOSE 80 5000

# Comando de inicialização
CMD ["sh", "-c", "service nginx start && python app.py"]
