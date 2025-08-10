# Tight Coupling vs Loose Coupling – Java Example

This project demonstrates the difference between **tight coupling** and **loose coupling** in Java using a simple example of fetching user details from a data source.

---

## 📌 Tight Coupling

In tight coupling:

Classes are directly dependent on each other’s concrete implementations.

Example:
UserManager creates an instance of UserDatabase directly and calls its methods.

java
Copy
Edit
private UserDatabase userDatabase = new UserDatabase();
Problem: If the data source changes (e.g., switch from MySQL to MongoDB or Web Service), you must modify the UserManager code.

Impact:

Low flexibility

Hard to maintain

Not easily scalable

## 📌 Loose Coupling
In loose coupling:

Classes depend on abstractions (interfaces/abstract classes), not concrete implementations.

Example:

UserDataProvider interface defines a contract for fetching user details.

Different implementations:

UserDatabaseProvider – Fetches data from a database.

WebServiceDataProvider – Fetches data from a web service.

NewDatabaseProvider – Example for adding another data source.

UserManager depends on UserDataProvider:

java
Copy
Edit
private UserDataProvider userDataProvider;

public UserManager(UserDataProvider provider) {
    this.userDataProvider = provider;
}
Benefit: Adding a new data source only requires:

Creating a new class that implements UserDataProvider.

Passing it to UserManager at runtime.

Impact:

High flexibility

Easier to maintain

Scales without modifying existing code

## 📌 Key Takeaways
Tight coupling makes systems rigid and hard to change.

Loose coupling promotes flexibility, maintainability, and scalability.

Use interfaces or abstract classes to decouple components.
