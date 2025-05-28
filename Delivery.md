Duygu İrem Kılıç
170422027

https://github.com/duyguiremkilic/OpenAPI_REST_API_Tasarim.git


API Açıklaması
Varlıklar (Entities)
API'de üç temel varlık bulunmaktadır:

Books: Kütüphanedeki kitaplar (id, title, author, isbn, publisher, pageCount, stock)

Students: Üniversite öğrencileri (id, name, studentNumber, email, isActive)

Loans: Kitap ödünç alma işlemleri (id, studentId, bookId, loanDate, returnDate, status)

CRUD Endpointleri
Books:

GET /books - Tüm kitapları listeler (sayfalanmış)

POST /books - Yeni kitap eklemek için

GET /books/{id} - Tek kitap detayı için

PUT /books/{id} - Kitap bilgilerini güncellemek için

DELETE /books/{id} - Kitabı silmek için

Students:

GET /students - Tüm öğrencileri listelemek için

POST /students - Yeni öğrenci eklemek için

GET /students/{id} - Tek öğrenci detayı

PUT /students/{id} - Öğrenci bilgilerini güncellemek için

DELETE /students/{id} - Öğrenciyi silmek için

Loans:

GET /loans - Tüm ödünç kayıtlarını listelemek için

POST /loans - Yeni ödünç kaydı oluşturmak için

GET /loans/{id} - Tek ödünç kaydı detayı

PATCH /loans/{id}/return - Kitap iade işlemi için

Components Kullanımı
schemas: Tüm varlıkların modelleri ve input modelleri tanımlandı.
parameters: id (path), page ve size (query) parametreleri ortak kullanım için tanımlandı.

responses: 400 (BadRequest), 404 (NotFound) ve 500 (ServerError) standart hata yanıtları oluşturuldu.

Sayfalama ve Hata Durumları
GET /books endpointinde page ve size parametreleri ile sayfalama desteklendi.

Tüm endpointlerde uygun HTTP status kodları ve hata mesajları tanımlandı.

Zorunlu alanlar ve format kontrolleri (UUID, email, ISBN-13) eklendi.

🧪 Test Notları
GET /books Çağrısı
Başarılı yanıt: 200 OK

İçerik: Kitap listesi (sayfalanmış)

Örnek:

[
  {
    "id": "123e4567-e89b-12d3-a456-426614174000",
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "isbn": "978-0743273565",
    "publisher": "Scribner",
    "pageCount": 180,
    "stock": 5
  }
]
POST /students Request Body

{
  "name": "Duygu Kilic",
  "studentNumber": "20222426",
  "email": "ayse.demir@university.edu"
}
Hatalı İstek Örneği (400 Bad Request)
Geçersiz email formatı:


{
  "error": "Invalid input data",
  "details": "email must be a valid email address"
}
