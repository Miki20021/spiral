FROM node:16-alpine3.15
RUN addgroup -S spiralgroup && adduser -S spiral -G spiralgroup
WORKDIR /app
RUN chown -R spiral:spiralgroup /app
USER spiral
COPY --chown=spiral:spiralgroup package.json ./
RUN npm install --only=production && npm audit fix
COPY --chown=spiral:spiralgroup . .
ENTRYPOINT ["npm"]
CMD ["run", "start"]
