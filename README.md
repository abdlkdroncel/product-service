# Product Service

Product Service, MongoDB veritabanı kullanarak ürün yönetimi sağlayan bir RESTful API'dir. Spring Boot 3.5.9 ile geliştirilmiştir.

## 📋 İçindekiler

- [Özellikler](#özellikler)
- [Teknolojiler](#teknolojiler)
- [Gereksinimler](#gereksinimler)
- [Kurulum](#kurulum)
- [Kullanım](#kullanım)
- [API Endpoints](#api-endpoints)
- [Test](#test)
- [Konfigürasyon](#konfigürasyon)

## ✨ Özellikler

- ✅ Ürün oluşturma
- ✅ Tüm ürünleri listeleme
- ✅ MongoDB ile veri saklama
- ✅ RESTful API mimarisi
- ✅ Testcontainers ile entegrasyon testleri
- ✅ Lombok ile boilerplate kod azaltma

## 🛠 Teknolojiler

- **Java 17**
- **Spring Boot 3.5.9**
- **Spring Data MongoDB**
- **MongoDB**
- **Lombok**
- **Maven**
- **Testcontainers**
- **JUnit 5**

## 📦 Gereksinimler

Projeyi çalıştırmak için aşağıdaki yazılımların sisteminizde kurulu olması gerekmektedir:

- Java 17 veya üzeri
- Maven 3.6+
- MongoDB 4.4+
- Docker (Testler için - Testcontainers kullanımı)

## 🚀 Kurulum

### 1. Projeyi Klonlayın

```bash
git clone <repository-url>
cd product-service
```

### 2. MongoDB'yi Başlatın

MongoDB'nin çalıştığından emin olun. Docker kullanarak çalıştırabilirsiniz:

```bash
docker run -d \
  --name mongodb \
  -p 27017:27017 \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=admin123 \
  mongo:4.4.2
```

### 3. Bağımlılıkları Yükleyin

```bash
./mvnw clean install
```

### 4. Uygulamayı Çalıştırın

```bash
./mvnw spring-boot:run
```

Uygulama varsayılan olarak `http://localhost:8080` adresinde çalışacaktır.

## 💻 Kullanım

### Ürün Modeli

```json
{
  "id": "string",
  "name": "string",
  "description": "string",
  "price": "number"
}
```

## 🔌 API Endpoints

### 1. Yeni Ürün Oluşturma

**POST** `/api/v1/product`

**Request Body:**
```json
{
  "name": "iPhone 13",
  "description": "iPhone 13 Pro Max",
  "price": 1200.00
}
```

**Response:** `201 Created`

**cURL Örneği:**
```bash
curl -X POST http://localhost:8080/api/v1/product \
  -H "Content-Type: application/json" \
  -d '{
    "name": "iPhone 13",
    "description": "iPhone 13 Pro Max",
    "price": 1200.00
  }'
```

### 2. Tüm Ürünleri Listeleme

**GET** `/api/v1/product`

**Response:** `200 OK`

```json
[
  {
    "id": "507f1f77bcf86cd799439011",
    "name": "iPhone 13",
    "description": "iPhone 13 Pro Max",
    "price": 1200.00
  }
]
```

**cURL Örneği:**
```bash
curl -X GET http://localhost:8080/api/v1/product
```

## 🧪 Test

Proje, Testcontainers kullanarak MongoDB ile entegrasyon testleri içermektedir.

### Testleri Çalıştırma

```bash
./mvnw test
```

**Not:** Testler için Docker'ın çalışıyor olması gerekmektedir. Testcontainers, testler sırasında otomatik olarak MongoDB container'ı başlatır ve durdurur.

### Test Yapısı

- **Integration Tests:** MongoDB ile gerçek veritabanı etkileşimlerini test eder
- **MockMvc:** REST API endpoint'lerini test eder

## ⚙️ Konfigürasyon

### application.properties

Uygulamanın varsayılan konfigürasyonları:

```properties
spring.application.name=product-service

# MongoDB Configuration
spring.data.mongodb.host=localhost
spring.data.mongodb.port=27017
spring.data.mongodb.database=productdb
spring.data.mongodb.username=admin
spring.data.mongodb.password=admin123
spring.data.mongodb.authentication-database=admin
```

### Ortam Değişkenleri

Farklı ortamlar için aşağıdaki ortam değişkenlerini kullanabilirsiniz:

```bash
export MONGODB_HOST=localhost
export MONGODB_PORT=27017
export MONGODB_DATABASE=productdb
export MONGODB_USERNAME=admin
export MONGODB_PASSWORD=admin123
```

## 📁 Proje Yapısı

```
product-service/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/kadir/productservice/
│   │   │       ├── controller/
│   │   │       │   └── ProductController.java
│   │   │       ├── dto/
│   │   │       │   ├── ProductRequest.java
│   │   │       │   └── ProductResponse.java
│   │   │       ├── model/
│   │   │       │   └── Product.java
│   │   │       ├── repository/
│   │   │       │   └── ProductRepository.java
│   │   │       ├── service/
│   │   │       │   └── ProductService.java
│   │   │       └── ProductServiceApplication.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/
│           └── com/kadir/productservice/
│               └── ProductServiceApplicationTests.java
├── pom.xml
└── README.md
```

## 🤝 Katkıda Bulunma

1. Bu projeyi fork edin
2. Feature branch'i oluşturun (`git checkout -b feature/amazing-feature`)
3. Değişikliklerinizi commit edin (`git commit -m 'feat: Add amazing feature'`)
4. Branch'inizi push edin (`git push origin feature/amazing-feature`)
5. Pull Request oluşturun

## 📝 Lisans

Bu proje açık kaynaklıdır.

## 📧 İletişim

Proje Sahibi - Abdul Kadir Öncel

Proje Linki: [https://github.com/yourusername/product-service](https://github.com/yourusername/product-service)

---

⭐️ Bu projeyi beğendiyseniz yıldız vermeyi unutmayın!

