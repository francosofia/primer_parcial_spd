# primer_parcial_spd

# Integrantes
Franco Sofia

# Proyecto : Montacargas
![Tinkercard](
![Parte Práctica Domiciliaria franco sofia ](https://github.com/francosofia/primer_parcial_spd/assets/108673571/932afb06-d4f0-44c4-93b9-615d26c1a4aa))


#Descripcion
El montacargas sube  al precionar el boton "Subir" y al precionar el boton "Parar", el mismo se detiene y muestra el piso en el cual se paro, para  bajar el mismo se debe precionar el boton "bajar" , al llegar al piso 0 te lo comunica , ademas   enciende una led verde cuando esta en movimiento y una led roja cuando esta detenida y muestra el piso en el que estas por un display de 7 segmentos y por consola .

#Funcion principal
Este codigo tiene tres funciones principales y son la funcion "subir","bajar"y
"parar" que son los botones que  hacen que funcione  el montacargas.


void subir(int lectura,int boton)
{
 
 lectura = digitalRead(boton);
  if(lectura == 1)
	 {
   
  	 flag = true;
    
	 }

   	if(flag == true)
 	 {
     
      apagar_led(LED_ROJO);
      prender_led(LED_VERDE);
      
      for(acumulador = auxiliar;acumulador < 10;acumulador ++)
      {
         if(acumulador<= 9 && acumulador > 0)
       {
           
         auxiliar = acumulador;
       }

        parar(lectura_dos,BOTON_DOS,B);
        
        Serial.println("estas subiendo  y estas en el psio");
        
        Serial.println(acumulador);
       
          parar(lectura_dos,BOTON_DOS,B);
        
        piso();
        delay(1000);
        
        parar(lectura_dos,BOTON_DOS,B);
      }
      
      flag = false;
    }
 }


void bajar(int lectura, int boton)
{

  lectura = digitalRead(boton);
  if (lectura == 1)
  {
    
    flag_tres = true;
    apagar_led(LED_ROJO);
    prender_led(LED_VERDE);
  }
  if (flag_tres == true)
  {

    if( acumulador > 10)
     {
      acumulador = auxiliar;
     }
    
    for (acumulador = auxiliar;acumulador > 0; acumulador--)
    {
     
      parar(lectura_dos, BOTON_DOS,A);
    
      piso();
      
      parar(lectura_dos, BOTON_DOS,A);
     
      Serial.println("esta bajando el montacargas");
     
      parar(lectura_dos, BOTON_DOS,A);
    
      if (acumulador == 0)
      {
       
        Serial.println("llegaste al piso 0");
      }
   
      flag_tres = false;
    }
  }
}

#void parar(int lectura,int boton,int a)
{
   lectura = digitalRead(boton);
  if (lectura == 1)
  {
    flag_segunda = true;
  }
  if(flag_segunda == true)
  { 
 apagar_led(LED_VERDE);
 prender_led(LED_ROJO);
   piso();
   acumulador = a;
    Serial.println("se paro el montacargas");
    flag_segunda = false;
  }
  
}

# Diagrama esquematico del circuito

![Diagrama esquematico del circuito](https://github.com/francosofia/primer_parcial_spd/assets/108673571/3d921dd7-e2c2-4369-9933-ba5187c99b9a)



# Posibles errores

Por la forma en la que  se programo el montacargas  no detecta de forma correcta al precionar el boton  parar , en caso de q no se detecte  se debve mantener apretado  hasta que pare




















