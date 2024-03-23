class Book:
    def __init__(self, title, author, year, status="Available"):
        self.title = title
        self.author = author
        self.year = year
        self.status = status

    def __str__(self):
        return f"{self.title} by {self.author} ({self.year}) - Status: {self.status}"

class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)

    def search_book(self, title):
        for book in self.books:
            if book.title.lower() == title.lower():
                return book
        return None

    def borrow_book(self, title):
        book = self.search_book(title)
        if book:
            if book.status == "Available":
                book.status = "Borrowed"
                return f"{book.title} has been borrowed."
            else:
                return f"{book.title} is not available for borrowing."
        else:
            return f"{title} is not found in the library."

def main():
    library = Library()

    book1 = Book("Python Programming", "John Doe", 2020)
    book2 = Book("Data Science Essentials", "Jane Smith", 2019)
    book3 = Book("Web Development Basics", "Sam Green", 2021)

    library.add_book(book1)
    library.add_book(book2)
    library.add_book(book3)

    print("Library Catalog:")
    for book in library.books:
        print(book)

    print("\nBorrowing a book:")
    print(library.borrow_book("Python Programming"))
    print(library.borrow_book("Web Development Basics"))
    print(library.borrow_book("Data Science Essentials"))

    print("\nUpdated Library Catalog:")
    for book in library.books:
        print(book)

if __name__ == "__main__":
    main()
