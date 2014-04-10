.. documentacion modulos DYPRA documentation master file, created by
   sphinx-quickstart on Mon Apr  7 17:10:44 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to documentacion modulos DYPRA's documentation!
=======================================================

Contents:

.. toctree::
   :maxdepth: 2

Introducción
Los modulos y adaptaciones que se detallan a continuacion se realizaron sobre sobre el ERP Tryton 3.0 para Medios El Independiente Coopegraf Ltda de La Rioja.
Manteniendo estandares y genericidad para que pueda replicarse y reusarse en otros medios similares.





Modificaciones y Adaptacion
============================

Producto
--------

Posee las categorías y productos necesarios para la gestion de medios:
   * Diario:
       * Aviso Común
       * Aviso Especial
       * Clasificado
       * Funebre
       * Edicto
       * Suplemento
       * Insert
       * Centímetros
   * Radio:
	   * Costo Provincial
	   * Costo Nacional
	   * Costo Oficial
   * Digital:
	   * Costo Provincial
	   * Costo Nacional
	   * Costo Oficial

Ademas se provee un fichero que inserta los productos correspondientes en cada tipo, con su precio de lista, precio de costo ($0 ya que son servicios) e impuestos asociado. 
En cuanto a unidades de medida de los productos estan provistos:
   * cm: Para los productos de tipo Aviso Común, Clasificado Destacado, Fúnebre Destacado.
   * línea: Para los productos de tipo Clasificado por Línea
   * página: Para los productos de tipo Suplemento Módulo Completo.
   * unidad: Para los productos de tipo Aviso Especial, Edicto Judicial, Insert, Radio y Digital.

El producto especial,”Bonificación” se genero para facilitar descuentos en las ventas.


