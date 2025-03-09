# Этап сборки
FROM python:3.10
WORKDIR /app

# Копируем только файл зависимостей для предварительной установки
COPY requirements.txt .

# Устанавливаем зависимости
RUN pip install -r requirements.txt --no-cache-dir

# Копируем весь проект
COPY . .

# Запускаем приложение
CMD ["python", "manage.py", "runserver", "0:8000"]
