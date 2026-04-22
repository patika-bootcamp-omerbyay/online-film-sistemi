# online-film-sistemi
OOP - Online Film Sistemi</br>

Uygulamada filmler listelenebilir, sıralanabilir ve kullanıcılar uygulamaya abone olabilir.</br>
Kullanıcılar abonelik için sistem üzerinden kredi satın alır.</br>
Sadece abone olan kullanıcılar, kredileri ile film kiralayabilir ve kiraladığı filmin kredi bedeli kadar hesabından düşülür.</br>
Normal kullanıcılar ve aboneler film satın alabilirler.</br>
Eğer film mevcut değil ise talep edilebilir.</br></br>

```mermaid
classDiagram
    class Kullanici {
        -String id
        -String ad
        -String email
        +filmSatinAl()
        +filmTalepEt()
        +aboneOl()
    }

    class Abone {
        -double kredi
        +krediSatinAl()
        +filmKirala()
    }

    class Film {
        -String id
        -String ad
        -String tur
        -double fiyat
        -int krediBedeli
        -boolean mevcutMu
    }

    class Uygulama {
        +filmleriListele()
        +filmleriSirala()
    }

    class SatinAlma {
        -String islemId
        -DateTime tarih
        -double tutar
    }

    class Kiralama {
        -String islemId
        -DateTime baslangicTarihi
        -DateTime bitisTarihi
        -int harcananKredi
    }

    class Talep {
        -String talepId
        -DateTime tarih
        -String filmAdi
    }

    Abone --|> Kullanici : kalıtım

    Uygulama *-- Film : barındırır
    Uygulama *-- Kullanici : barındırır

    Kullanici --> SatinAlma : oluşturur
    Kullanici --> Talep : oluşturur
    SatinAlma --> Film : satın alınır
    Abone --> Kiralama : oluşturur
    Kiralama --> Film : kiralanır
    Talep --> Film : talep edilir

```


Polimorfizm notu: Abone, Kullanici'dan türediği için filmSatinAl() metodunu miras alır. Ek olarak filmKirala() ve krediSatinAl() davranışlarına sahiptir.
