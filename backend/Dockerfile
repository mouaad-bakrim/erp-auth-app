# Étape 1 : image Python officielle légère
FROM python:3.11-slim

# Variables d’environnement pour un comportement Python adapté à la prod
ENV PYTHONUNBUFFERED=1
ENV DJANGO_SETTINGS_MODULE=auth_service.settings

# Crée et se place dans le dossier de travail
WORKDIR /app

# Copie les fichiers de dépendances
COPY requirements.txt .

# Installe les dépendances Python
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Copie tout le code dans le container
COPY . .

# Expose le port 8000 (celui utilisé par Django par défaut)
EXPOSE 8000

# Commande de lancement (gunicorn pour la prod)
CMD ["gunicorn", "auth_service.wsgi:application", "--bind", "0.0.0.0:8000"]
