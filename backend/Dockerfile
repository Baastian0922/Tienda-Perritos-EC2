# ETAPA 1: Builder (Compilación)
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
# Si usas TypeScript o Nest, descomenta la siguiente línea:
# RUN npm run build

# ETAPA 2: Runner (Producción)
FROM node:18-alpine
WORKDIR /app
# REQUISITO: Usuario No-Root [cite: 91, 129]
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
ENV NODE_ENV=production

# Copiamos solo lo necesario de la etapa anterior
COPY --from=builder /app/package*.json ./
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/ . 

# Seguridad: Cambiamos permisos y switch de usuario
RUN chown -R appuser:appgroup /app
USER appuser

EXPOSE 3001
CMD ["npm", "start"]
