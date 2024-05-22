# Giriş

### DDD Nedir?

Domain-Driven design (DDD), karmaşık yazılım projelerinde karmaşıklığı azaltmak için kullanılan bir yazılım geliştirme metodolojisidir. Bu metodoloji, yazılımın karmaşıklığını azaltmak için yazılımı domain (alan) odaklı bir şekilde geliştirmeyi amaçlar. Domain, yazılımın işlevsel gereksinimlerini ve iş süreçlerini tanımlayan bir kavramdır.

DDD, yazılımın domain odaklı bir şekilde geliştirilmesi için bir dizi prensip ve yöntem sunar.

Domain Driven Design var olan ve yaşanan problemlerin _Domain_ esas alınarak analiz edilmesi ve çözülmesi gerektiğini savunan ve bunun için Domain’in net bir şekilde anlaşılmasının gerekli olduğunu söyleyen bir felsefedir.

### Önemli faydaları

    1.	Projeyi Anlaşılabilir Hale Getirir: DDD, projenin karmaşık terminolojisini ve bilgilerini herkesin anlayabileceği bir hale getirir. Bu sayede hem geliştiriciler hem de diğer ekip üyeleri aynı dili konuşur ve anlaşmazlıklar azalır.
    2.	Tahmin Edilebilirlik Sağlar: DDD, projelerin kapsamını ve gereksinimlerini net bir şekilde tanımlar. Bu sayede proje süresi ve gereksinimleri daha doğru tahmin edilebilir hale gelir, sürprizlerle karşılaşma olasılığı azalır.
    3.	Standartlaştırma Sağlar: DDD, kod yazımında belirli kurallar ve standartlar getirdiği için geliştiriciler kodun ne yaptığını daha hızlı anlar ve projeye yeni katılanlar için adapte olma süreci kısalır.
    4.	Karmaşıklığı Azaltır: Büyük projelerde ortaya çıkan karmaşıklık DDD ile yönetilebilir hale gelir. Projenin farklı alanları (domain) belirli bölümlere ayrılarak her bir alanın kendi içinde daha basit ve yönetilebilir olması sağlanır.
    5.	Sürdürülebilirlik Sağlar: DDD ile geliştirilen projeler, uzun vadede daha sürdürülebilir olur. Kodun daha kolay bakım yapılabilir ve geliştirilebilir hale gelmesi sayesinde, zaman içinde oluşan teknik borçlar azalır.
    6.	Ekip İşbirliğini Güçlendirir: DDD, tüm ekip üyelerinin proje hakkında daha fazla bilgi sahibi olmasını ve işbirliği yapmasını sağlar. Bu sayede, ekip içi iletişim artar ve projede daha verimli çalışılır.
    7.	Esneklik Sağlar: Proje sürecinde yeni ihtiyaçlar veya değişiklikler ortaya çıktığında, DDD sayesinde bu değişiklikler daha kolay ve hızlı bir şekilde projeye entegre edilebilir.

### Stratejik DDD ve Taktiksel DDD

DDD, genellikle stratejik DDD ve taktiksel DDD olmak üzere iki ana bölüme ayrılır.

Stratejik DDD, domain'i tanımlayan ve domain arasındaki ilişkileri belirleyen bir bölümdür. Örnek olarak, domain içindeki bounded context'leri, aggregate'leri ve aggregate root'ları belirler.

Taktiksel DDD ise, domain içindeki nesnelerin nasıl tasarlanacağını ve nasıl bir araya getirileceğini belirleyen bir bölümdür. Örnek olarak, entity'leri, value object'leri, repository'leri ve factory'leri belirler.

### DDD'nin Temel Kavramları

örnek bir e-ticaret uygulaması üzerinden DDD'nin temel kavramlarını açıklayalım.

1. **Domain (Alan):** Yazılımın işlevsel gereksinimlerini ve iş süreçlerini tanımlayan bir kavramdır. Domain, yazılımın odaklandığı alanı ifade eder.

örneğimizdeki e-ticaret uygulamasında, müşteri, sipariş, ürün, kategori gibi kavramlar domain'i tanımlar. Bu kavramlar, e-ticaret uygulamasının işlevsel gereksinimlerini ve iş süreçlerini tanımlar.

2. **Ubiquitous Language (Her Yerde Aynı Dil):** Yazılım geliştirme sürecinde, yazılım geliştiricileri, iş analistleri ve diğer paydaşlar arasında ortak bir dil oluşturulmalıdır. Bu dil, yazılımın domain'ini tanımlayan bir dil olmalıdır.

örnek:

- Müşteri: Bir müşteriyi temsil eden bir sınıf.
- Sipariş: Bir siparişi temsil eden bir sınıf.

3. **Bounded Context (Sınırlı Bağlam):** Domain'i tanımlayan bir kavramdır. Bounded Context, bir domain'i tanımlayan sınırlı bir bağlamı ifade eder ve domain içindeki farklı alanları temsil eder.

örnek: e-ticaret uygulamasında, müşteri, sipariş, ürün, kategori gibi kavramlar farklı bounded context'lerde yer alabilir. Her bounded context, belirli bir alanı temsil eder ve bu alanın sınırlarını belirler. Mesela, müşteri ve sipariş kavramları bir bounded context içinde yer alabilirken, ürün ve kategori kavramları başka bir bounded context içinde yer alabilir.

4. **Aggregate (Küme):** Domain'deki nesnelerin bir araya getirilmesiyle oluşturulan bir kavramdır. Aggregate, birbirleriyle ilişkili nesnelerin bir araya getirilmesiyle oluşur.

örnek: Bir e-ticaret uygulamasında, müşteri ve sipariş nesneleri bir aggregate oluşturabilir. Bu aggregate, müşteri ve sipariş nesnelerini bir araya getirerek, müşteri ve sipariş arasındaki ilişkiyi yönetebilir.

```java
public class Customer {
    private String id;
    private String name;
    private List<Order> orders;
}

public class Order {
    private String id;
    private Customer customer;
    private List<OrderItem> items;
}

public class OrderItem {
    private String id;
    private Product product;
    private int quantity;
}
```

5. **Aggregate Root (Küme Kök):** Aggregate içindeki nesneler arasındaki ilişkiyi yöneten ve aggregate'i temsil eden bir nesnedir. Aggregate Root, aggregate içindeki nesneler arasındaki ilişkiyi yönetir ve aggregate'i dış dünyaya temsil eder.

örnek: Yukarıdaki örnekte, Customer sınıfı bir aggregate root olabilir. Customer sınıfı, müşteri ve sipariş nesneleri arasındaki ilişkiyi yönetir ve aggregate'i temsil eder.

6. **Entity (Varlık):** Domain'deki nesneleri temsil eden bir kavramdır. Entity, domain'deki nesnelerin birer temsilcisidir ve genellikle bir kimlik (ID) ile tanımlanır.

örnek: Yukarıdaki örnekte, Customer, Order ve OrderItem sınıfları birer entity olabilir. Bu sınıflar, domain'deki müşteri, sipariş ve sipariş kalemi kavramlarını temsil eder.

7. **Value Object (Değer Nesnesi):** Domain'deki nesnelerin değerlerini temsil eden bir kavramdır. Value Object, domain'deki nesnelerin değerlerini temsil eder ve genellikle immutable (değişmez) olarak tasarlanır. Value Object'ler genellikle entity'lerin içinde kullanılır.

örnek: Yukarıdaki örnekte, Product sınıfı bir value object olabilir. Product sınıfı, bir ürünün özelliklerini temsil eder ve immutable olarak tasarlanabilir.

bir başka örnek:

```java
public class Address {
    private String street;
    private String city;
    private String zipCode;
}
```

8. **Repository (Depo):** Domain'deki nesnelerin veritabanı ile ilişkisini yöneten bir kavramdır. Domain nesnelerinin veritabanı ile ilişkisini soyutlar ve nesnelerin veritabanı ile ilişkisini gizler.

şu şekilde bir örnek verilebilir:

```java
public interface CustomerRepository {
    Customer findById(String id);
    void save(Customer customer);
    void delete(Customer customer);
}

public class JpaCustomerRepository implements CustomerRepository {
    private EntityManager entityManager;

    public Customer findById(String id) {
        return entityManager.find(Customer.class, id);
    }

    public void save(Customer customer) {
        entityManager.persist(customer);
    }

    public void delete(Customer customer) {
        entityManager.remove(customer);
    }
}
```

9. **Factory (Fabrika):** Domain nesnelerinin oluşturulmasını ve inşa edilmesini sağlayan bir kavramdır. Factory, domain nesnelerinin oluşturulmasını soyutlar ve nesnelerin oluşturulmasını gizler.

örnek:

```java
public class CustomerFactory {
    public Customer createCustomer(String name) {
        Customer customer = new Customer();
        customer.setName(name);
        return customer;
    }
}
```

10. **Service (Hizmet):** Domain'deki iş mantığını temsil eden bir kavramdır. Service, domain'deki iş mantığını soyutlar ve iş mantığını gizler.

örnek:

```java
public class OrderService {
    private OrderRepository orderRepository;

    public void createOrder(Customer customer, List<OrderItem> items) {
        Order order = new Order();
        order.setCustomer(customer);
        order.setItems(items);
        orderRepository.save(order);
    }
}
```

11. **Event (Olay):** Domain'deki olayları temsil eden bir kavramdır. Event, domain'deki olayları temsil eder ve olayların yayılmasını sağlar.

örnek: Bir sipariş oluşturulduğunda, OrderCreatedEvent adında bir olay yayılabilir.

```java
public class OrderCreatedEvent {
    private Order order;

    public OrderCreatedEvent(Order order) {
        this.order = order;
    }

    public Order getOrder() {
        return order;
    }
}

public class OrderService {
    private OrderRepository orderRepository;
    private EventBus eventBus;

    public void createOrder(Customer customer, List<OrderItem> items) {
        Order order = new Order();
        order.setCustomer(customer);
        order.setItems(items);
        orderRepository.save(order);

        OrderCreatedEvent event = new OrderCreatedEvent(order);
        eventBus.publish(event);
    }
}

public class OrderCreatedEventHandler {
    public void handle(OrderCreatedEvent event) {
        Order order = event.getOrder();
        // Order created event handling logic
    }
}
```

Bu event, diğer servisler tarafından dinlenerek, sipariş oluşturulduğunda yapılması gereken işlemleri gerçekleştirebilir.

Eventler farklı bounded context'ler arasında iletişimi sağlar.
