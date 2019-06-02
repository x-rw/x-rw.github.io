---
layout: post
title: Desing Patterns
---

Some time ago when i study in university i was programer creating many instance of objects, for example: to BUSCAMINAS game i create explicitly the objects, new Flag(), new Mine(), new Table(), new Casilla(), etc.

Next with the analogy that a box is a bomb or is a flag, then my creations was bad bad bad..., why create explicitly? is better delegate this funcionality to other class, and BOOM BOMM this class is the Factory, the Factory should to take over to create objects.


public interface  Producto {  
   public void accion();
 }

 public class Producto1 implements Producto{

  @Override 
  public void accion() { 
     System.out.print("MENSAJE DE PRODUCTO 1");
  }
}




public class Producto2 implements Producto{

    @Override
    public void accion() {
        System.out.print("MENSAJE DE PRODUCTO 2");
    }
    
}

public class Producto3 implements Producto{

    @Override
    public void accion() {
        System.out.print("MENSAJE DE PRODUCTO 3");
    }
}

public enum Type {
    PRODUCTO1, PRODUCTO2, PRODUCTO3;
}


public abstract class Factory {

    public Producto crear(Type type) {
        Producto producto=null;
        switch (type) {
            case PRODUCTO1:
                producto=new Producto1();
                break;
            case PRODUCTO2:
                producto=new Producto2();
                break;
            case PRODUCTO3:
                producto=new Producto3();
                break;
            default:
        }
        return producto;
    }
}


public class FactoryMethod extends Factory{

  public FactoryMethod(){
   super();
  }
  
}


public class App {
    public static void main(String args []){
        FactoryMethod factoryMethod=new FactoryMethod();
        Producto producto=factoryMethod.crear(Type.PRODUCTO1);
        System.out.println("SE CREO EL PRODUCTO "+ producto.getClass().getName());
    }
}

