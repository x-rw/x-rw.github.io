---
layout: post
title: Singleton
---
The objects  need one instance, because if we instantiate more than one this produces  problems same incorrect program behavior, overuse of resources, or
inconsistent results.

There are only two points in the definition of a singleton design pattern

* There should be only one instance allowed for a class and
* We should allow global point of access to that single instance.

public class Singleton {

    private static Singleton instance = new Singleton();

    private Singleton() {
        System.out.println("creating");
        if (instance != null) {
            throw new RuntimeException("Ya existe una instancia ");
        }
    }

    public static Singleton getInstance() {
        return instance;
    }

    public static void main(String[] args) throws Exception {
        Singleton S1 = Singleton.getInstance();
        print(S1.getClass().getName(), S1);
        Singleton S2 = Singleton.getInstance();
        print(S2.getClass().getName(), S2);
    }

    public static void print(String name, Singleton singleton) {
        System.out.println(name + "  " + singleton.hashCode());
    }

}
