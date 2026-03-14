# Базовый образ Python 3.9 slim
FROM python:3.9-slim

# Рабочая директория
WORKDIR /app

# Обновляем список пакетов и устанавливаем системные зависимости
RUN apt-get update && apt-get install -y curl vim

# Копируем файл зависимостей
COPY requirements.txt .

# Устанавливаем Python-пакеты
RUN pip install --no-cache-dir -r requirements.txt

# Создаём пользователя appuser с UID 1000
RUN useradd -u 1000 -m -s /bin/bash appuser

# Переключаемся на пользователя appuser
USER appuser

# Копируем основной файл приложения
COPY app.py .

# Открываем порт 5000
EXPOSE 5000

# Устанавливаем переменную окружения
ENV FLASK_ENV=production

# Запускаем приложение
CMD ["python", "app.py"]
