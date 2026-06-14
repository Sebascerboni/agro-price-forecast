# ─── Stage 1: Build React ───────────────────────────────────────────────────
FROM node:20-alpine AS build

WORKDIR /web

COPY web/package*.json ./
RUN npm ci

COPY web/ .
ENV VITE_API_URL='/'
RUN npm run build

# ─── Stage 2: Production (FastAPI) ──────────────────────────────────────────
FROM python:3.12-slim AS prod

WORKDIR /api

COPY api/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY api/ .

COPY --from=build /web/dist ./static

EXPOSE 8000

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
