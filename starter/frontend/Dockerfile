FROM  public.ecr.aws/docker/library/node:18.14.2-alpine3.17

ARG REACT_APP_MOVIE_API_URL
ENV REACT_APP_MOVIE_API_URL=${REACT_APP_MOVIE_API_URL}

WORKDIR /app

RUN ls -lsha

# Copy dependdency files
COPY package*.json ./

RUN ls -lsha

# Install packages
RUN npm ci

# Copy code
COPY . .

RUN ls -lsha
RUN ls -lsha ./components/MovieList
RUN echo --
RUN ls -lsha /app/src/components/MovieList

# Build the app
RUN npm run build

# Expose the port used by the React app
EXPOSE 3000

# Start the React app when the container starts
CMD ["npm", "run", "serve"]