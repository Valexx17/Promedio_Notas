 package NOTAS_ESTUDIANTES;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class CalculadoraNotas {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("¿Cuántas notas desea calcular? : ");
        int cantidadNotas = sc.nextInt();

        Notas notas = new Notas();

        for (int D = 1; D <= cantidadNotas; D++) {
            System.out.println("Ingresa la nota " + D + ":");
            double Nota = sc.nextDouble();
            notas.ingresarNota(Nota);

            double suma = notas.calcularSuma();
            double promedio = notas.calcularPromedio();

            System.out.println("El total de las notas es: " + suma);
            System.out.println("El promedio de las notas es: " + promedio);

            for (double nota : notas.getNotas()) {
                if (nota < promedio) {
                    System.out.println("La nota " + nota + " está por debajo del promedio.");
                } else {
                    System.out.println("La nota " + nota + " está por encima del promedio.");
                }
            }
        }

        sc.close();  
    }

    static class Notas {
        private double sumaTotal;
        private int cantidadNotas;
        private final List<Double> notas = new ArrayList<>();

        public void ingresarNota(double nota) {
            sumaTotal += nota;
            cantidadNotas++;
            notas.add(nota);
        }

        public double calcularSuma() {
            return sumaTotal;
        }

        public double calcularPromedio() {
            if (cantidadNotas == 0) {
                return 0.0;
            }
            return sumaTotal / cantidadNotas;
        }

        public List<Double> getNotas() {
            return notas;
        }
    }
}
