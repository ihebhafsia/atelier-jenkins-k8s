Dockerfile
# --- ÉTAPE 1: Build Stage (Compilation) ---
FROM gcc:11 AS build
WORKDIR /app
COPY . .
# Supposons que votre programme est compilé avec gcc -o serveur
RUN gcc -o serveur serveur.c
# --- ÉTAPE 2: Final Stage (Image Légère) ---
FROM alpine:latest
WORKDIR /usr/local/bin
# Copie uniquement le binaire compilé
COPY --from=build /app/serveur .
# Spécifiez la commande d'exécution
CMD ["./serveur", "6000"]# --- ÉTAPE 1: Build (Compilation) ---
FROM gcc:11 AS build

WORKDIR /app
COPY . .

# Compile le serveur
RUN gcc -o serveur serveur.c

# --- ÉTAPE 2: Image finale légère ---
FROM alpine:latest

WORKDIR /usr/local/bin

# On copie seulement le binaire
COPY --from=build /app/serveur .

# Port logique du serveur
EXPOSE 5000

# Commande de lancement
CMD ["./serveur", "6000"]

