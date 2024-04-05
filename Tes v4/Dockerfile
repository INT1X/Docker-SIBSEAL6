FROM golang:1.22.0-alpine3.19

# Set the Current Working Directory inside the container
WORKDIR /app

# Copy go.mod dan go.sum ke direktori kerja di dalam container
COPY go.mod go.sum ./

# Download semua dependensi. Dependensi akan di-cache jika go.mod dan go.sum tidak berubah
RUN go mod download

# Copy semua file dari direktori proyek ke direktori kerja di dalam container
COPY . .

# Mendapatkan paket-paket yang diperlukan oleh aplikasi Go
RUN go get github.com/go-redis/redis/v8
RUN go get go.mongodb.org/mongo-driver/mongo
RUN go get go.mongodb.org/mongo-driver/mongo/options

# Build aplikasi Go
RUN go build -o main .

# Expose port 8080 untuk akses ke aplikasi HTTP
EXPOSE 8080

# Menjalankan aplikasi saat container dimulai
CMD ["./main"]
