# Excepciones_en_Java
package excepciones;
import java.io.IOException;
import java.util.Scanner;

/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

/**
 *
 * @author Adirane
 */

public class OpcionErroneaException extends Exception{
    
    public OpcionErroneaException(){
    }
    
    public String mensaje(){
        return ("OPCION ERRONEA");
    }
}

class LeerDatos3 {
    
    public static void main(String[] args) throws IOException{
        
        Scanner teclado = new Scanner(System.in);
        
        String numero = " ";
        String continua = " ";
        
        try
        {
           do
           {
               System.out.println("Introduzca un numero: ");
               numero = teclado.next();
               int num = Integer.parseInt(numero);
               
               if(num % 2 == 0)
               {
                   System.out.println("El numero: " + num + " es par.");
               } else{
                   System.out.println("El numero: " + num + " es impar.");
               }
               
               System.out.println("¿Desea continuar? S/N");
               continua = teclado.next();
               
               if(continua.equals("s") && !continua.equals("n")){
                   throw new OpcionErroneaException();
               }
           } while(continua.equals("s") || continua.equals("S"));
           
        } catch (NumberFormatException e){
            System.out.println("Debe introducir numeros.");
        } catch (OpcionErroneaException e){
            System.out.println(e.mensaje());
        }
    }
    
}
