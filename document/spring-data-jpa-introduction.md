# Giới thiệu về Spring Data JPA



### Giới thiệu JPA

- Java Persistence API hay JPA là một đăc tả Java cho việc ánh xạ giữa các đối tượng Java tới cơ sở dữ liệu quan hệ sử dụng cộng nghệ phổ biến là ORM( Object Relational Mapping).
- Cung cấp đầy đủ các công cụ cho phép người lập trình có thể tạo cơ sở dữ liệu một cách đơn giản và nhanh chóng.
- JPA là một đăc tả của Sun, ra đời cùng với bản đặc tả J2EE 5.
- JPA không phải là một sản phẩm và không thể dùng nó như thành phần persistence. Nó cần phải có một cài đặt ORM để hoạt động và persist các đối tượng Java. 

#### Một số lợi ích của JPA

- Đơn giản hóa công nghệ cho tầng persistence (tầng dữ liệu)
- Không phụ thuộc vào các framework ORM
- Có nhiều nhà cung cấp hỗ trợ cài đặt JPA
- Dữ liệu có thể được lưu trữ thông qua việc ORM

#### Một số ORM framework hỗ trợ JPA

Dưới đây là danh sách các framework ORM có thể dùng với đặc tả JPA

* Hibernate
* EclipseLink
* Open JPA.

#### Tại sao nên dùng JPA

- Viết ít code hơn
- Performance tốt
- Độc lập về database
- Không phải làm việc với SQL



### Kiến trúc JPA

#### Các khái niệm trong JPA

Khái niệm JPA bao gồm ba thành phần chính là Entity, EntityManager và EntityManagerFactory

* Entity
  * Là các đối tượng persistence thể hiện một mẫu tin trong cơ sở dữ liệu.
  * Chỉ là các lớp POJO đơn giản, dễ dàng tạo
  * Một số đặc điểm của Entity:
    * Entity có thể tương tác với cơ sở dữ liệu quan hệ.
    * Entity được xác định thông qua một định danh (tương đương với khóa chính trong table của cơ sở dữ liệu quan hệ)
    * Entity hỗ trợ giao tác (transaction)
    * Entity hỗ trợ kế thừa giống như những lớp thường khác.
* EntityManager
  * Là một giao diện (interface) cung cấp các API cho việc tương tác với các Entity.
  * Một số chức năng cơ bản:
    * Persist: phương thức này dùng để lưu một thực thể mới tạo vào cơ sở dữ liệu.
    * Merge: dùng để cập nhật trạng thái của entity vào cơ sở dữ liệu.
    * Remove: xóa một thể hiện của entity.
* EntityManagerFactory
  * EntityManagerFactory được dùng để tạo ra một thể hiện của EntityManager

#### Các tính năng của JPA

* JPA hỗ trợ pluggable, tức là có thể sử dụng nhiều nhà hãng cung cấp thứ ba như Hibernate hay Toplink.
* Hỗ trợ annotation
* Giảm bớt số lớp yêu cầu cho việc phát triển persistence.
* Không cần phải viết các mô tả triển khai trong xml. Annotation dựa trên metadata đã hỗ trợ trong các ứng dụng JPA.
* Đã chuẩn hóa ORM và dễ dàng phát triển hơn
* JPA hỗ trợ truy vấn động và tĩnh.
* Nhiều IDE hỗ trợ phát triển ứng dụng JPA và có thể tự động sinh code ánh xạ từ cơ sở dữ liệu thành các entity và ngược lại.



### Spring Data Repositories

Bạn có thể sử dụng Spring data JPA mà không cần phải phải hiện thực bất cứ một repository abstract nào. Nhưng để làm được điều đó bạn phải làm quen với các Spring data repository interface. Các interface được chia làm 2 nhóm chính:

**1. Spring Data Commons bao gồm các interface**

- Repository<T, ID extends Serializable> interface nắm bắt entity cần quản lý và kiểu dữ liệu id của entity đó.

- CrudRepository<T, ID extends Serializable> interface cung cấp các phương thức CRUD cho việc quản lý các entity.

- PagingAndSortingRepository<T, ID extends Serializable> interface khai báo các phương thức hỗ trợ việc sắp  xếp, phân trang dữ liệu từ database.

- QueryDslPredicateExecutor interface thì không phải là một repository interface. Nó khai báo các phương thức được sử dụng để lấy các entity từ database bằng việc sử dụng các đối tượng QueryDsl Predicate. 

**2. Spring Data JPA gồm các interface:**

- JpaRepository<T, ID extends Serializable> interface là một JPA repository cụ thể, nó kết hợp với các phương thức được khai báo trong các common repository interface.

- JpaSpecificationExecutor interface không phải là một repository interface, nó khai báo các phương thức được sử dụng để lấy các entity từ database bằng việc sử dụng các đối tượng Specification của JPA criteria API.


![SpringDataRepositories Image](http://btit95.esy.es/source/springdatajrepositories.png?1480866710906)



