# 반복자 패턴
### 반복자 패턴(Iterator pattern)이란?
반복자 패턴(iterator pattern)은 객체 지향 프로그래밍에서 반복자를 사용하여 컨테이너를 가로지르며 컨테이너의 요소들에 접근하는 디자인 패턴이다. 반복자 패턴은 컨테이너로부터 **알고리즘을 분리**시키며, 일부의 경우 알고리즘들은 필수적으로 컨테이너에 특화되어 있기 때문에 분리가 불가능하다.
`출처 - 위키피디아`

## 예시
#### Book.class
```
public class Book {
    private String name;

    public Book(String name) {
          this.name = name;
    }

    public String getName() {
        return name;
    }
}
```
#### Aggregate.interface
```
public interface Aggregate {

    public abstract Iterator createIterator();
}
```	

#### BookShelf .class
```
public class BookShelf implements Aggregate {
    private Book[] books; // 책의 집합
    private int last = 0; // 마지막 책이 꽂힌 위치

    public BookShelf(int size) {
        books = new Book[size];
    }

    public Book getBook(int index) {
        return books[index];
    }

    public int getLength() {
        return last;
    }

    // 책꽂이에 책을 꽂는다
    public void appendBook(Book book) {
        if (last < books.length) {
            this.books[last] = book;
            last++;
        } else {
            System.out.println("책꽂이가 꽉 찼습니다!");
        }
    }

    @Override
    public Iterator createIterator() {
        return new BookShelfIterator(this);
    }
}
```

#### BookShelfIterator.class
```
public class BookShelfIterator implements Iterator<Book> {
    private BookShelf bookShelf; // 검색을 수행할 책꽂이
    private int index = 0; // 현재 처리할 책의 위치

    public BookShelfIterator(BookShelf bookShelf) {
        this.bookShelf = bookShelf;
    }

    @Override
    public boolean hasNext() {
        return index < bookShelf.getLength();
    }

    @Override
    public Book next() {
        Book book = bookShelf.getBook(index);
        index++;
        return book;
    }
}
```

#### Main.class
```
public class Main {

    public static void main(String[] args) {
        BookShelf bookShelf = new BookShelf(10);

        Book book1 = new Book("Bilbe");
        Book book2 = new Book("Cinderella");
        Book book3 = new Book("Daddy-Long-Legs");

        bookShelf.appendBook(book1);
        bookShelf.appendBook(book2);
        bookShelf.appendBook(book3);

        System.out.println("현재 꽂혀있는 책 : " + bookShelf.getLength() + "권");

        Iterator it = bookShelf.createIterator();
        while (it.hasNext()) {
            Book book = (Book) it.next();
            System.out.println(book.getName());
        }
    }
}
```
                                             
---
## 왜 반복자 패턴인가
```
for (int i = 0; i < bookShelf.getLength(); i++) {
    System.out.println(bookShelf.getBook(i).getName());
}
```
이렇게 좋은 코드를 두고 왜 반복자 패턴을 사용하냐면, **하나씩 꺼내서 처리하는 과정을 구현과 분리**할 수 있기 때문이다. 반복자 패턴을 사용한다면 이 코드는
```
while (it.hasNext()) {
    Book book = (Book) it.next();
    System.out.println(book.getName());
}
```
이렇게 되는데, 이렇게 된다면 BookShelf의 구현에서 사용되고 있는 메서드는 호출되지 않는다. 즉, BookShelf의 구현에 **의존성**이 사라지게 된다.
