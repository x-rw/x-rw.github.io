---
layout: post
title: Facade Patterns
categories: [bloggy]
---

Muchas veces se tiene varias clases que uno al mirarlos no sabe cual es el orden de cada clase, en el ejemplo de abajo se muestra 3 clases: "CPU, Memory, HardDrive", la pregunta es: cuando se realiza una accion, cual es el orden de ejecucion de ellas?, para solucionar y mantener un orden se crea una FACHADA que organice el orden y de esa manera simplifique las acciones del subsistema. 

![My helpful screenshot](/images/facade.png)


```java
class CPU {
    public void freeze() { ... }
    public void jump(long position) { ... }
    public void execute() { ... }
}

class Memory {
    public void load(long position, byte[] data) { ... }
}

class HardDrive {
    public byte[] read(long lba, int size) { ... }
}
```

La FACHADA es el encargado de ejecutar la funcion start() para que el procesador, la ram se ejecuten de manera sincronizada.
```java
class ComputerFacade {
    private CPU processor;
    private Memory ram;
    private HardDrive hd;

    public ComputerFacade() {
        this.processor = new CPU();
        this.ram = new Memory();
        this.hd = new HardDrive();
    }

    public void start() {
        processor.freeze();
        ram.load(BOOT_ADDRESS, hd.read(BOOT_SECTOR, SECTOR_SIZE));
        processor.jump(BOOT_ADDRESS);
        processor.execute();
    }
}
```
