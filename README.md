# Actividad-Programacion-Funcional
ESTUDIANTE: ASTRID VIVIANA NOVA CORREA 
INGENIERIA DE SISTEMAS
Descripción del problema: Gestión de inventario de una tienda
Descripción de los datos: productos, precios, stock
interfaces funcionales usadas:Predicate, Function, Consumer
Instrucciones para compilar y ejecutar el programa:comandos java y java
Ejemplo de los resultados esperados:<img width="1000" height="637" alt="image" src="https://github.com/user-attachments/assets/bf13bb81-f711-4f43-9ff8-9cf7337f4c4e" />
Declaración sobre el uso de herramientas de IA: si use talk al, para apoyarme en la estructura de código y redacción

CODIGO TIENDA FUNCIONAL:
import java.util.List;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Predicate;

public class TiendaFuncional {

    // Definición de los datos mediante un record (inmutable y limpio)
    public record Producto(String nombre, double precio, int stock, String categoria) {}

    public static void main(String[] args) {
        // 1. Datos iniciales con los que trabajará el programa
        List<Producto> inventario = List.of(
            new Producto("Laptop Gamer", 1200.0, 5, "Tecnología"),
            new Producto("Mouse Inalámbrico", 25.5, 30, "Tecnología"),
            new Producto("Silla Ergonómica", 180.0, 8, "Hogar"),
            new Producto("Cafetera Eléctrica", 45.0, 15, "Hogares"),
            new Producto("Audífonos Bluetooth", 60.0, 20, "Tecnología")
        );  
    

        System.out.println("=== SISTEMA DE GESTIÓN Y ANÁLISIS DE PRODUCTOS ===");
        System.out.println("Total de productos en inventario: " + inventario.size() + "\n");

        // =========================================================================
        // REQUISITO 2 y 3: Uso de Predicate<T> para evaluar una condición
        // =========================================================================
        // Qué recibe: Un objeto de tipo Producto.
        // Qué operación realiza: Evalúa si el precio del producto es mayor a 100.0.
        // Qué resultado devuelve: Un valor booleano (true si es costoso, false si no).
        Predicate<Producto> esCostoso = p -> p.precio() > 100.0;

        System.out.println("--- 1. Evaluación de Productos Costosos (Predicate) ---");
        for (Producto prod : inventario) {
            boolean cumple = esCostoso.test(prod);
            System.out.println("¿El producto '" + prod.nombre() + "' cuesta más de $100? -> " + cumple);
        }
        System.out.println();

        // =========================================================================
        // REQUISITO 2 y 4: Uso de Function<T, R> para transformar un dato
        // =========================================================================
        // Qué recibe: Un objeto de tipo Producto.
        // Qué operación realiza: Aplica un descuento del 10% (multiplica el precio por 0.9).
        // Qué resultado devuelve: Un Double que representa el nuevo precio con descuento.
        Function<Producto, Double> calcularDescuento = p -> p.precio() * 0.90;

        System.out.println("--- 2. Transformación: Precios con 10% de Descuento (Function) ---");
        for (Producto prod : inventario) {
            double precioConDescuento = calcularDescuento.apply(prod);
            System.out.printf("Producto: %-20s | Precio Original: $%.2f | Precio con Descuento: $%.2f%n",
                    prod.nombre(), prod.precio(), precioConDescuento);
        }
        System.out.println();

        // =========================================================================
        // REQUISITO 2 y 5: Uso de Consumer<T> para procesar/consumir información
        // =========================================================================
        // Qué recibe: Un objeto de tipo Producto.
        // Qué operación realiza: Imprime en consola un reporte detallado del producto en formato amigable.
        // Qué resultado devuelve: No devuelve nada (void), solo ejecuta una acción de salida.
        Consumer<Producto> mostrarReporteProducto = p -> {
            System.out.println(" [Reporte de Stock] " + p.nombre() + 
                               " | Categoría: " + p.categoria() + 
                               " | Stock disponible: " + p.stock() + " unidades");
        };

        System.out.println("--- 3. Procesamiento y Consumo de Información (Consumer) ---");
        // Se aplica el Consumer a cada elemento utilizando forEach
        inventario.forEach(mostrarReporteProducto);
          }
}
<img width="1891" height="981" alt="Screenshot 2026-11-12 135116" src="https://github.com/user-attachments/assets/f1f1e852-c082-470b-834a-90f6cb58bd06" />
<img width="1598" height="880" alt="Screenshot 2026-11-12 135147" src="https://github.com/user-attachments/assets/9d7bbb89-51d2-450d-8eee-bb044ac1e45b" />
<img width="1535" height="423" alt="Screenshot 2026-11-12 135206" src="https://github.com/user-attachments/assets/606981cc-2830-40e7-adab-c5e25c486415" />








        
    }
}
