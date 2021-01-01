MVC (Model-View-Controller), yazdığımız uygulamanın iş mantığı ile (business logic) kullanıcı arayüzünü birbirinden ayrıştıran, uygulamanın farklı amaçlara hizmet eden kısımlarının birbirine girmesini engelleyen yazılım mimarisidir.Kodun farklı amaçlara hizmet eden yapılarını birbirinden ayırarak, kodu daha rahat geliştirilebilir ve test edilebilir (yani daha az hata çıkartma potansiyeline sahip) hale getirmiş oluruz.
Pek çok MVC nedir makalesi Web tabanlı projelerden örnek verse de, Desktop/Mobil uygulama geliştirirken de MVC kullanılabilir. Zira MVC bir mimari biçimdir. (Örneğin iOS geliştiriciler iPhone uygulaması geliştirirken MVC modelini kullanır)

**Model**

Uygulamada kullanılan verileri temsil eder ve verilerin işlenme mantığının saklandığı kısımdır. (Verilerin validasyonu burada yapılır)
Genelde verilerin veritabanı (veya XML gibi benzer bir yere) kaydedilmesi ve kayıtlı yerden alınması işlemleri yine burada olabilir. (Genelde dedim, şu an detaya girmeyeceğim. Daha sonraki yazılarda bu konuyu detaylıca inceleyeceğim.)

**View**

View, MVC’de projenin arayüzlerinin oluşturulduğu bölümdür. Bu bölümde projenin kullanıcılara sunulacak olan HTML dosyaları yer almaktadır. Projenin geliştirildiği yazılım dillerine göre dosya uzantıları da değişebilmektedir. Projelerin büyüklüğüne göre dikkat edilmesi gereken bir nokta ise, klasörlemedir.
Eğer bir web projesi geliştiriyorsanız, projenin View’larının yer aldığı klasörlerinin hiyerarşisi, ilerleyen dönemlerde karmaşıklığa sebep olmaması için dikkatli yapılmalıdır. Kimi yazılım geliştiriciler web projelerinde HTML dosyaları ile Javascript, CSS ve resim dosyalarını aynı klasör içinde barındırmaktadır. Ufak bir ayrıntı gibi görünse de projenin ilerleyen dönemlerinde ciddi problemler oluşturmaktadır.
View’ın bir görevi de, kullanıcılardan alınan istekleri controller’a iletmektir.

**Controller**

Model ve View arasında getir götür işlemlerini gerçekleştirir.
Kullanıcıların View üzerinden gerçekleştirdiği işlemlerle alınan veriyi Model’e taşır, Model’den aldığı veriyi View üzerinden kullanıcıya gösterir.
MVC yapısında ana mantık Model ve View yapısının ayrılmasıdır. Bu iki yapı arasındaki haberleşmeyi sağlayan köprüye Controller diyoruz.

**Peki neden MVC mimarisini kullanmalıyız?**

MVC sayesinde Model ve View yapısını ayrıştırmış oluyoruz.

Böylelikle yarın bir gün uygulamamızın görünümünü değiştirmek durumunda kaldığımızda “yalnızca” görünümle uğraşmamız gerekecek. İç içe geçmiş, spagetti bir kodla uğraşmak durumunda kalmış olsaydık, sadece görünümü değiştirmek isterken uygulamanın “işleyişini” de değiştirmemiz gerekecekti. (Hatta bunu yaparken işleyişi de yanlışlıkla bozabilirdik)

Ayrıca, bu ayrıştırma sayesinde Model ve View yapımızda ihtiyaç duyduğumuz parçaları, başka projelerde de tekrar kullanılabilir hale getirmiş olduk. Sonuçta, yazılım geliştirmede yegane amacımız “hatadan uzak olmak” ve “zamandan tasarruf etmek”.

**MVC’nin Yaşam Döngüsü(Life Cycle)**

**1) HTTP Request:** Sizin her ASP.NET MVC uygulamasını görüntülemek istemeniz bir request(istek) tir.
Bu istediğinizi HTTP üzerinden IIS tarafından alınır. Her yaptığınız istek Server tarafından bir yanıtla
son bulması gerekir.

**2) Routing:** ASP.NET MVC uygulamasını her istek yaptığınızda, yaptığınız yanıt UrlRoutingModule
HTTP Module tarafından durdurulur. UrlRoutingModule bir isteği durdurduğu zaman, gelen istek
RouteTable’dan hangi Controller tarafından üstleneceğine karar verilir.

**3) Controller:** RouteTable’dan gelen route bilgisine göre Controller hangi Action’ı çalıştıracaksa o
View çalıştırılır. View, Controller tarafından render edilmez. Controller tarafından geriye ViewResult
döndürülür.

**4) ViewResult:** ViewResult, View’i render etmek için aktif View Engine’i çağırır.

**5) ViewEngine :** Bir CSHTML dosyayı oluşturduğunuzda içerisindeki script ve markuplar, Razor View
Engin tarafından bazı ASP.NET API’lerini sayfalarınızı HTML’e çevirmek için kullanır.

**6) View:** View Engine tarafından HTML’e çevirilen kodlar kullanıcıya sunulur.

**7) Response:** HTTP üzerinden View kullanıcıya gösterilir.

[](https://www.google.com/url?sa=i&url=https%3A%2F%2Fbarisakbas.com.tr%2Fnet-core%2Fblog%2F30-asp-net-mvc-nedir-ne-ise-yarar.html&psig=AOvVaw0aYV6VdQ8LeYC_8wZ6aPK3&ust=1609625280684000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCOD85c3f--0CFQAAAAAdAAAAABAD)
