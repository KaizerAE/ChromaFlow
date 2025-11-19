# ========== Stage 1: Dependencies ==========
FROM node:20-alpine AS deps
WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm ci --only=production && \
    npm cache clean --force

# ========== Stage 2: Development ==========
FROM node:20-alpine AS development
WORKDIR /app

# Copy dependencies
COPY --from=deps /app/node_modules ./node_modules
COPY . .

# Install dev dependencies
RUN npm install

EXPOSE 8000

CMD ["npm", "run", "dev"]

# ========== Stage 3: Builder ==========
FROM node:20-alpine AS builder
WORKDIR /app

# Copy dependencies and source
COPY --from=deps /app/node_modules ./node_modules
COPY . .

# Build TypeScript
RUN npm run build

# ========== Stage 4: Production ==========
FROM node:20-alpine AS production
WORKDIR /app

ENV NODE_ENV production

# Create non-root user
RUN addgroup --system --gid 1001 nodejs && \
    adduser --system --uid 1001 nodejs

# Copy built files
COPY --from=builder /app/dist ./dist
COPY --from=deps /app/node_modules ./node_modules
COPY package*.json ./

USER nodejs

EXPOSE 8000

CMD ["node", "dist/index.js"]
