+++
date = '2026-01-03T15:36:37+03:00'
title = 'Java Object-Oriented Programming Encapsulation Explained'
+++

It has happened many times that I tried to learn OOP, but I somehow got stuck in tutorial hell and never really understood the logic behind it. Yes, I know that we need to create classes and reference them from other classes to separate different objects and responsibilities and make the code modular. But I always struggled when it came to writing code without any help. So let’s overcome this issue and truly learn OOP.

---

# Encapsulation

Let’s start with a simple example and build a small **inventory system**.

The goal here is not to build something complex, but to understand **how data is protected and accessed** in an object-oriented way.

---

## Main Class

```java
public class Main {
    public static void main(String[] args) {
        Inventory inventory = new Inventory();

        Item item1 = new Item("Sword", 1);
        Item item2 = new Item("Shield", 1);
        Item item3 = new Item("Health Potion", 5);

        inventory.addItem(item1);
        inventory.addItem(item2);
        inventory.addItem(item3);

        inventory.displayInventory();
    }
}
```
The Main class is the entry point of the application.
Here, we create objects and tell them what to do, but we don’t care how they do it internally.


**Item Class**

A Java class is a blueprint for creating objects.
Every object created from this class represents a single item in the inventory.

```java
public class Item {

    // Every object has its own properties
    private String name;
    private int quantity;

    // Constructor: runs once when a new object is created
    public Item(String name, int quantity) {
        this.name = name;
        this.quantity = quantity;
    }

    // Public methods are used to access private properties
    public String getName() {
        return name;
    }

    public int getQuantity() {
        return quantity;
    }
}
```
**Why is this Encapsulation?**

The fields name and quantity are private
They cannot be accessed directly from outside the class
Access is only possible through public methods

This means the internal state of an object is protected, and other classes can only interact with it in controlled ways.
This concept is called encapsulation.



**Inventory Class:**

```java
import java.util.ArrayList;

public class Inventory {
    private ArrayList<Item> items;

    public Inventory (){
        items = new ArrayList<>();
    }

    public void addItem(Item item){
        items.add(item);
    }

    public void displayInventory(){
        for(Item item:items){
            System.out.println("Item: " +item.getName() + ", Quantity: " + item.getQuantity());
        }
    }
}
```

The Inventory class is responsible for managing items, not for describing what an item is.

It stores items in a list
It exposes simple methods like addItem and displayInventory
It does not allow direct access to the internal list

This separation of responsibility makes the code easier to maintain and extend.


**Key Takeaway**

Encapsulation is not about hiding data for no reason.
It is about controlling access, protecting state, and making misuse harder.

You don’t need to understand all OOP principles at once.
If you clearly understand why fields are private and why we use public methods, you are already on the right path.
