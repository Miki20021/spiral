FROM node:16-alpine3.15
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
WORKDIR /app
RUN chown -R appuser:appgroup /app
USER appuser
COPY --chown=appuser:appgroup package*.json ./
RUN npm ci --only=production && npm audit fix
COPY --chown=appuser:appgroup . .
ENTRYPOINT ["npm"]
CMD ["run", "start"]
