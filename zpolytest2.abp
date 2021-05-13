*&---------------------------------------------------------------------*
*& Report ZPOLYTEST2
*&---------------------------------------------------------------------*
*&
*&---------------------------------------------------------------------*
REPORT ZPOLYTEST2.

"Ejemplo de encapsulamiento, herencia y polimorfismo en ABAP.

"Definimos una clase abstracta, podriamos llamarla una plantilla
"para las clases heredadas. Cuando definimos una clase como abstracta
"no tiene implementacion.
CLASS lcl_vehiculo DEFINITION ABSTRACT.

  PUBLIC SECTION.
    METHODS: obtener_tipo ABSTRACT,
             obtener_marca ABSTRACT,
             set_notas ABSTRACT
              IMPORTING notas TYPE string,
             ver_notas ABSTRACT
              EXPORTING notas TYPE string.

  PROTECTED SECTION.
    DATA: lv_notas TYPE string.

ENDCLASS.

***********************************************************************
"Definimos una clase lcl_auto que hereda lcl_vehiculo y redefine los
"metodos de la clase padre (lcl_vehiculo).
CLASS lcl_auto DEFINITION
               INHERITING FROM lcl_vehiculo.

  PUBLIC SECTION.
    "Los metodos con REDEFINITION son los originales de lcl_vehiculo.
    "Como podemos ver podemos agregar nuestros propios metodos
    "como por ejemplo cantidad_puertas que pertenece solo a esta clase.
    METHODS: obtener_tipo REDEFINITION,
             obtener_marca REDEFINITION,
             set_notas REDEFINITION,
             ver_notas REDEFINITION,
             cantidad_puertas.

ENDCLASS.

"Implementamos la clase lcl_auto con sus metodos.
CLASS lcl_auto IMPLEMENTATION.

  METHOD obtener_tipo.
    WRITE 'AUTO'.
  ENDMETHOD.

  METHOD obtener_marca.
    WRITE 'FORD'.
  ENDMETHOD.

  METHOD set_notas.
    lv_notas = notas.
  ENDMETHOD.

  METHOD ver_notas.
    WRITE lv_notas.
  ENDMETHOD.

  METHOD cantidad_puertas.
    WRITE '4'.
  ENDMETHOD.

ENDCLASS.

***********************************************************************
"Definimos una clase lcl_moto que hereda lcl_vehiculo y redefine los
"metodos de la clase padre (lcl_vehiculo).
CLASS lcl_moto DEFINITION
               INHERITING FROM lcl_vehiculo.

  PUBLIC SECTION.
    METHODS: obtener_tipo REDEFINITION,
             obtener_marca REDEFINITION,
             set_notas REDEFINITION,
             ver_notas REDEFINITION.

ENDCLASS.

"Implementamos la clase lcl_moto con sus metodos.
CLASS lcl_moto IMPLEMENTATION.

  METHOD obtener_tipo.
    WRITE 'MOTO'.
  ENDMETHOD.

  METHOD obtener_marca.
    WRITE 'HONDA'.
  ENDMETHOD.

  METHOD set_notas.
    lv_notas = notas.
  ENDMETHOD.

  METHOD ver_notas.
    WRITE lv_notas.
  ENDMETHOD.

ENDCLASS.

***********************************************************************
START-OF-SELECTION.

"Declaramos los objetos.
DATA: lo_autos TYPE REF TO lcl_auto,
      lo_motos TYPE REF TO lcl_moto.

"Creamos los objetos.
CREATE OBJECT lo_autos.
CREATE OBJECT lo_motos.

"Llamamos a los metodos que setean las notas.
CALL METHOD lo_autos->set_notas( 'ALGO Autos' ).
CALL METHOD lo_motos->set_notas( 'ALGO 2 Motos').

"Llamamos a los metodos que muestran la informacion.
WRITE 'TIPO:'.
CALL METHOD lo_autos->obtener_tipo( ).
NEW-LINE.
WRITE 'MARCA:'.
CALL METHOD lo_autos->obtener_marca( ).
NEW-LINE.
WRITE 'NOTAS:'.
CALL METHOD lo_autos->ver_notas( ).
NEW-LINE.
WRITE 'PUERTAS:'.
CALL METHOD lo_autos->cantidad_puertas( ).
NEW-LINE.
WRITE '**************'.
NEW-LINE.
WRITE 'TIPO:'.
CALL METHOD lo_motos->obtener_tipo( ).
NEW-LINE.
WRITE 'MARCA:'.
CALL METHOD lo_motos->obtener_marca( ).
NEW-LINE.
WRITE 'NOTAS:'.
CALL METHOD lo_motos->ver_notas( ).