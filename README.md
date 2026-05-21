# Solución actividad 07.

## Clase Concesionaria (main)

```java

package concesionaria;


public class Concesionaria {
    float pi = 3;//No va pi para este ejercicio
    int num = (int)pi;//No num pi para este ejercicio
    public static void main(String[] args) {
        
       
        Persona vendedor = new Persona("Juan Pérez", "33444555");
        Persona comprador = new Persona("Ana García", "40111222");

        
        Vehiculo auto1 = new Automovil("Toyota", "Corolla", 33000000, 4);
        Vehiculo moto1 = new Moto("Honda", "CB500F", 5400000, 500);

        
        Venta factura1 = new Venta(vendedor, comprador, auto1);

        System.out.println("--- Procesando Venta de Concesionaria ---");
        factura1.imprimirFactura();        
        System.out.println("\n------------------------------------------");
        
        
        Venta factura2 = new Venta(vendedor, comprador, moto1);
        factura2.imprimirFactura(); 
        
    } 
}

```

## Clase Vehiculo.

```java

package concesionaria;

public abstract class Vehiculo {
    protected String marca;
    protected String modelo;
    protected double precio;

    public Vehiculo() {
    }

    public Vehiculo(String marca, String modelo, double precio) {
        this.marca = marca;
        this.modelo = modelo;
        this.precio = precio;
    }
    public abstract void mostrarDetalles();
    
    public String getMarca() { return marca; }
    public String getModelo() { return modelo; }
    public double getPrecio() { return precio; }
}

```

## Clase Moto

```java
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package concesionaria;

/**
 *
 * @author agust
 */
public class Moto extends Vehiculo {
    private int cilindrada;
    
    public Moto(String marca, String modelo, double precio, int cilindrada) {
        super(marca, modelo, precio);
        this.cilindrada = cilindrada;
    }
    
    @Override
    public void mostrarDetalles() {
        System.out.println("Moto: " + marca + " " + modelo + 
                         " | Cilindrada: " + cilindrada + "cc" +
                         " | Precio: $" + precio);
    }
 
}

```

## Clase Automovil.

```java
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package concesionaria;

/**
 *
 * @author agust
 */
public class Automovil extends Vehiculo {
    private int cantidadPuertas;
    
    public Automovil(String marca, String modelo, double precio, int cantidadPuertas) {
        super(marca, modelo, precio);
        this.cantidadPuertas = cantidadPuertas;
    }

    @Override
    public void mostrarDetalles() {
        System.out.println("Auto: " + marca + " " + modelo + 
                         " | Puertas: " + cantidadPuertas + 
                         " | Precio: $" + precio);
    }
    
}

```

## Clase persona.

```java

package concesionaria;
public class Persona {
    private String nombre;
    private String dni;

    public Persona() {
    }

    public Persona(String nombre, String dni) {
        this.nombre = nombre;
        this.dni = dni;
    }

    public String getNombre() { return nombre; }
    public String getDni() { return dni; }
    
    @Override
    public String toString() {
        return nombre + " (DNI: " + dni + ")";
    }
    
}

```
## Clase Venta.
```java
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package concesionaria;

/**
 *
 * @author agust
 */
public class Venta {
    
    private Persona vendedor;
    private Persona comprador;
    private Vehiculo vehiculo;
    private static int contadorFacturas = 0;
    private int numeroFactura;
    
    public Venta(Persona vendedor, Persona comprador, Vehiculo vehiculo) {
        this.vendedor = vendedor;
        this.comprador = comprador;
        this.vehiculo = vehiculo;
        this.numeroFactura = ++contadorFacturas;
    }
    
    public void imprimirFactura() {
        System.out.println("FACTURA N°: " + numeroFactura);
        System.out.println("----------------------");
        System.out.println("VENDEDOR: " + vendedor);
        System.out.println("COMPRADOR: " + comprador);
        System.out.println("----------------------");
        System.out.println("VEHÍCULO VENDIDO:");
        vehiculo.mostrarDetalles();  // Polimorfismo en acción
        System.out.println("----------------------");
        System.out.println("TOTAL: $" + vehiculo.getPrecio());
    }
}

```
