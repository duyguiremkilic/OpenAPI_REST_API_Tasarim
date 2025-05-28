Üniversite Kütüphane Sistemi API Dokümantasyonu
📖 Genel Bakış
Bu proje, bir üniversite kütüphane sisteminin REST API spesifikasyonunu OpenAPI 3.1 standardı kullanarak tanımlamaktadır. API, kitapların, öğrencilerin ve ödünç alma işlemlerinin yönetimi için gerekli endpoint'leri içermektedir.

🚀 Özellikler
Kitap Yönetimi: Kitapların eklenmesi, görüntülenmesi, güncellenmesi ve silinmesi

Öğrenci Yönetimi: Öğrenci kayıt işlemleri

Ödünç Alma İşlemleri: Kitap ödünç alma ve iade etme süreçleri

Sayfalama Desteği: Büyük veri setleri için optimize edilmiş sayfalama

🔧 Teknik Detaylar
API Özellikleri
OpenAPI Versiyon: 3.1.0

Veri Formatı: JSON

Kimlik Doğrulama: (Opsiyonel) API Key veya JWT

Kullanılan Teknolojiler
OpenAPI 3.1 spesifikasyonu

Swagger UI dokümantasyonu

📚 Varlık Modelleri
Kitap Modeli
yaml
Book:
  type: object
  properties:
    id: {type: string, format: uuid}
    title: {type: string}
    author: {type: string}
    isbn: {type: string, pattern: '^\d{3}-\d{10}$'}
    publisher: {type: string}
    pageCount: {type: integer}
    stock: {type: integer}
    
Öğrenci Modeli

Student:
  type: object
  properties:
    id: {type: string, format: uuid}
    name: {type: string}
    studentNumber: {type: string}
    email: {type: string, format: email}
    isActive: {type: boolean}

Ödünç Modeli

Loan:
  type: object
  properties:
    id: {type: string, format: uuid}
    studentId: {type: string, format: uuid}
    bookId: {type: string, format: uuid}
    loanDate: {type: string, format: date}
    returnDate: {type: string, format: date, nullable: true}
    status: {type: string, enum: [ongoing, returned, late]}

🌐 API Endpoint'leri
HTTP Metodu	Endpoint	Açıklama
GET	/books	Tüm kitapları listeler
POST	/books	Yeni kitap ekler
GET	/books/{id}	Tek kitap detayı
PUT	/books/{id}	Kitap bilgilerini günceller
DELETE	/books/{id}	Kitabı siler
GET	/students	Tüm öğrencileri listeler
POST	/students	Yeni öğrenci ekler
GET	/students/{id}	Tek öğrenci detayı
PUT	/students/{id}	Öğrenci bilgilerini günceller
DELETE	/students/{id}	Öğrenciyi siler
GET	/loans	Tüm ödünç kayıtlarını listeler
POST	/loans	Yeni ödünç kaydı oluşturur
GET	/loans/{id}	Tek ödünç kaydı detayı
PATCH	/loans/{id}/return	Kitap iade işlemi
🛠️ Kurulum ve Kullanım

Swagger Editor ile görüntüleme:

bash
https://editor.swagger.io/
Adresine giderek openapi.yaml dosyasını import edebilirsiniz.

API Testi:

Postman veya benzeri bir API istemcisi kullanarak endpoint'leri test edebilirsiniz

Örnek istekler için DELIVERY.md dosyasına bakınız.

📜 Lisans
Bu proje MIT lisansı altında lisanslanmıştır. Detaylar için LICENSE dosyasına bakınız.

