# Этап сборки
FROM python:3.10 AS build
WORKDIR /code

# Копируем только файл зависимостей для предварительной установки
COPY requirements.txt .

# Устанавливаем зависимости
RUN pip install --no-cache-dir -r requirements.txt

# Копируем весь проект
COPY . .

# Этап выполнения
FROM python:3.10-alpine
ENV PYTHONUNBUFFERED=1
WORKDIR /code

# Копируем код и зависимости из этапа сборки
COPY --from=build /code /code

# Устанавливаем дополнительные пакеты, если необходимо (например, для работы с базой данных)
RUN apk add --no-cache gcc musl-dev

# Открываем порт, на котором будет работать приложение
EXPOSE 8000

# Запускаем приложение
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
