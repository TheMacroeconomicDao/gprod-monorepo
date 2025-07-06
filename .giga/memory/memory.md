# GPROD Project Memory

## Архитектура проекта
- Backend: NestJS + TypeScript + Prisma
- Frontend: React + Vite + Feature-Sliced Design
- Deployment: Kubernetes + GitHub Actions CI/CD
- Registry: GitHub Container Registry (ghcr.io)

## Проблемы и решения
### Health Check Rate Limiting (Решено)
- Проблема: Kubernetes health checks блокировались rate limiting (429 ошибки)
- Решение: Комбинация code fixes + оптимизация readiness/liveness probe конфигурации в deployment.yml
- Коммиты с фиксами: 58cc88be, e041966e, 20e7762e

## CI/CD Pipeline
- GitHub Actions workflow в `.github/workflows/deploy.yml`
- Автодеплой на push в main/develop ветки
- Target namespace: develop-gprod
- Host: api.dev.gprod.build.infra.gyber.org
- **Статус: РАБОТАЕТ КОРРЕКТНО** - успешные деплои с Telegram уведомлениями

## Текущие проблемы
- Нет активных проблем с пайплайном
- CI/CD пайплайн: возможные проблемы с base64 decode в kubectl config
- Образы не пересобираются должным образом 