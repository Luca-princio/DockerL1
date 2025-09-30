# Utiliser nginx pour servir la page statique
FROM nginx:alpine

# Nettoyer et copier les fichiers
RUN rm -rf /usr/share/nginx/html/*
COPY ./index.html /usr/share/nginx/html/index.html
COPY ./style.css /usr/share/nginx/html/styles.css

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
