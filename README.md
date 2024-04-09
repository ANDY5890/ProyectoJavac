# ProyectoJavac
Proyecto en el cual se ingresaran 3 coordenadas para dar solución al área y perímetro, dando como solución la clasificación de tipos de  triángulos , Escaleno, Isósceles, Equilátero 
import javax.swing.JOptionPane;
// double son variables
//math .sqer para sacar la raiz cuadrada
// pow potencia
// acos arco coseno

/**
 *
 * @author Andy Alpizar
 */
public class VerticesDeUnTriangulo {

    public static void main(String[] args) {
        //Solicita al usario las coordenadas de los tres vertices 
        double x1 = Double.parseDouble(JOptionPane.showInputDialog("Introduce la coordenada x del primer vértice:"));
        double y1 = Double.parseDouble(JOptionPane.showInputDialog("Introduce la coordenada y del primer vértice:"));
        double x2 = Double.parseDouble(JOptionPane.showInputDialog("Introduce la coordenada x del segundo vértice:"));
        double y2 = Double.parseDouble(JOptionPane.showInputDialog("Introduce la coordenada y del segundo vértice:"));
        double x3 = Double.parseDouble(JOptionPane.showInputDialog("Introduce la coordenada x del tercer vértice:"));
        double y3 = Double.parseDouble(JOptionPane.showInputDialog("Introduce la coordenada y del tercer vértice:"));
        
        
        // Distacia entre puntos calcular longitudes del los lados del triangulo
        double lado1 = distanciaEntrePuntos(x1, y1, x2, y2);
        double lado2 = distanciaEntrePuntos(x2, y2, x3, y3);
        double lado3 = distanciaEntrePuntos(x3, y3, x1, y1);
        
        
        
        String tipo = determinarTipoTriangulo(lado1, lado2, lado3);
        
        double perimetro = lado1 + lado2 + lado3;
        
        double semiPerimetro = perimetro / 2;
        double area = Math.sqrt(semiPerimetro * (semiPerimetro - lado1) * (semiPerimetro - lado2) * (semiPerimetro - lado3));
        
        //para calcular el ángulo opuesto al lado
        double angulo1 = calcularAngulo(lado1, lado2, lado3);
        double angulo2 = calcularAngulo(lado2, lado3, lado1);
        double angulo3 = calcularAngulo(lado3, lado1, lado2);
       
        
        
        JOptionPane.showMessageDialog(null, "Tipo de triángulo: " + tipo
                                            + "\nPerímetro: " + perimetro
                                            + "\nÁrea: " + area
                                            + "\nÁngulo 1: " + Math.toDegrees(angulo1) + " grados"
                                            + "\nÁngulo 2: " + Math.toDegrees(angulo2) + " grados"
                                            + "\nÁngulo 3: " + Math.toDegrees(angulo3) + " grados");
    }
    public static double distanciaEntrePuntos(double x1, double y1, double x2, double y2) {
        return Math.sqrt(Math.pow((x2 - x1), 2) + Math.pow((y2 - y1), 2));
    }
   
    public static String determinarTipoTriangulo(double lado1, double lado2, double lado3) {
        if (lado1 == lado2 && lado2 == lado3) {
            return "Equilátero";
        } else if (lado1 == lado2 || lado2 == lado3 || lado1 == lado3) {
            return "Isósceles";
        } else {
            return "Escaleno";
        }
    }
   
    public static double calcularAngulo(double a, double b, double c) {
        return Math.acos((b * b + c * c - a * a) / (2 * b * c));
    }
}
