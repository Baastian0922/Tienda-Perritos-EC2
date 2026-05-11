# Usamos Nginx Alpine por ser liviano y seguro
FROM nginx:alpine

# REQUISITO: Capas limpias (Eliminamos contenido por defecto) [cite: 91]
RUN rm -rf /usr/share/nginx/html/*

# Copiamos tus archivos estáticos directamente al servidor
COPY index.html app.js /usr/share/nginx/html/

# Copiamos tu configuración de Nginx (asegúrate de que el archivo exista)
COPY default.conf /etc/nginx/conf.d/default.conf

# Exponemos el puerto estándar para tráfico web [cite: 56]
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]