.. documentacion modulos DYPRA documentation master file, created by
   sphinx-quickstart on Mon Apr  7 17:10:44 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


Documentacion DYPRA
===================

Introducción
============

Las modificaciones, adaptaciones y módulos que se detallan a continuación se realizaron sobre sobre el ERP Tryton 3.0 para Medios El Independiente Coopegraf Ltda de La Rioja para gestión de comercialización. Manteniendo la mayor estandarización y genericidad posible para que pueda replicarse y reusarse en otros medios similares.


Modificaciones y Adaptaciones
=============================

Las modificaciones y adaptaciones se realizaron sobre los módulos oficiales de Tryton,como por ejemplo en Producto, Entidad y Contabilidad.

Producto
--------

El módulo Producto posee las categorías y productos necesarios para la gestión de medios:

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

.. figure:: img/catproductos.png
   :width: 750 px

Además contiene un script que agrega los productos correspondientes en cada clasificación, con su precio de lista, precio de costo ($0 ya que son servicios) e impuestos asociados. Así como un producto especial, "Bonificación" provisto para facilitar descuentos en las ventas.

.. image:: img/productos.png
   :width: 750 px

En cuanto a unidades de medida de los productos estan definidas:

   * cm: Para los productos de tipo Aviso Común, Clasificado Destacado, Fúnebre Destacado.
   * línea: Para los productos de tipo Clasificado por Línea
   * página: Para los productos de tipo Suplemento Módulo Completo.
   * unidad: Para los productos de tipo Aviso Especial, Edicto Judicial, Insert, Radio y Digital.


Entidad
--------

El módulo Entidad provee las categorías necesarias para registrar clientes para áreas de Efectivo y Cuenta Corriente, del siguiente modo:

   * Cliente
   * Cliente/Particular
   * Cliente/Cuenta Corriente
   * Cliente/Cuenta Corriente/Comisionista
   * Cliente/Cuenta Corriente/Particular
   * Cliente/Cuenta Corriente/Oficial


.. image:: img/catclientes.png
   :width: 750 px

Tambien cuenta con el campo DNI para que pueda ser considerado en los filtros de búsqueda, asi como el tipo de facturación que se le realizará al cliente (B o A) para distinguir los reportes de Facturas con IVA incluido o discriminado.

.. image:: img/altacliente.png
   :width: 750 px


Ventas
------

La plantilla de ventas cuenta una pantalla inicial que permite la selección de uso de venta común que es la que posee Tryton por defecto o la posibilidad de facilitarse con el asistente de venta desarrollado.

.. image:: img/ventainicial.png
   :width: 750 px

La opción asistente venta es un wizard que consta de cuatro o más pasos que simplifican los cálculos de ventas de avisos y asigna fechas de aparición de los mismos. 

En general, se puede seleccionar al principio el tipo de venta: Efectivo o Cuenta Corriente.

Y se sigue según sea:

Efectivo:
"""""""""
Se busca un cliente asociado a ventas en efectivo, el tipo de servicio que se va a vender (Diario, Radio o Digital), y la categoría (como las mencionadas más arriba). Luego se pasa a seleccionar el producto (ya filtrado por el criterio anterior) y el origen. De acuerdo al producto se registran datos particulares del aviso, como cantidades (cm x col, líneas, paginas o unidades),importes, ubicación, bonificación (porcentual y fija), texto que se desea publicar, y tipo de apariciones (Dia/s Específico/s, Semanal/es, Mensual/es o Anual), con lo cual se especifica la fecha de inicio, y en caso de ser días específicos como pueden ser discontinuos se pasa a seleccionar fecha por fecha lo cantidad requerida.

Paso 1

.. image:: img/efectivopasouno.png
   :width: 750 px

Paso 2

.. image:: img/efectivopasodos.png
   :width: 750 px

Paso 3

.. image:: img/efectivopasotres.png
   :width: 750 px

Paso 4

.. image:: img/efectivopasocuatro.png
   :width: 750 px


Cuenta Corriente:
"""""""""""""""""
Idem que en el caso de Efectivo, solo que se listan algunas categorías de Diario, más una categoría especial que es Centimetros, para el caso que la venta sea por una cantidad determinada de centímetros a cuenta corriente (especificando cantidad de cm, col, y precio por cm)

.. image:: img/ctactecms.png
   :width: 750 px


Al finalizar, en ambos casos se habrá creado una venta en estado “Presupuesto”, con las líneas de venta (una por cada aviso vendido), mas una linea de venta de tipo comentario que contiene el texto a publicar y una línea adicional en caso de poseer bonificación que realiza el descuento sobre el importe total.

.. image:: img/ventaefectivopresup.png
   :width: 750 px

Cada línea de venta (de producto) posee una pestaña o apartado en la vista, que posee la publicación presupuestada asociada (ya sea para Diario, Radio o Digital), para que pueda modificarse algunos datos antes de confirmarse la venta.

.. image:: img/publicpresup.png
   :width: 750 px

.. image:: img/publicpresupdetalle.png
   :width: 750 px

En caso de confirmar la venta, si se trata de una venta en Efectivo se genera la factura asociada, y se pasan todas las publicaciones presupuestadas a las correspondientes publicaciones en el módulo de Edición (provisto con tal fin). Y a diferencia, cuando es por Cuenta Corriente, las facturas se generan recién cuando se marca como publicado dicho aviso.


Contabilidad
------------

La plantilla de facturas posee la posibilidad de elegir el tipo: A o B.
Ademas se puede generar un reporte resumido de factura que colapsa las líneas de factura que provienen de las líneas de ventas de avisos semanales, mensuales o anuales para una mejor visualización.
Y en caso de ser ventas del área de Cuenta Corriente la factura no se realiza al procesar la orden como generalmente se configura sino que se registran por aviso publicado.

.. image:: img/facturaresumida.png
   :width: 750 px


Nuevos Módulos
==============

Edición
-------

El módulo de Edición consta de una plantilla "Edición" que es un conjunto de fechas (que corresponden a las ediciones), y poseen el listado de publicaciones de los distintos medios ya sea Diario, Radio y Digital que están previstas para dicha edición.

.. image:: img/ediciones.png
   :width: 750 px

.. image:: img/publicacionesedicion.png
   :width: 750 px


Tambien se encuentran las plantillas: 
   * Publicaciones Diario,
   * Publicaciones Radio y 
   * Publicaciones Digitales

.. image:: img/menu.png
   :width: 750 px


Publicaciones Diario
""""""""""""""""""""

En esta opción se encuentra el listado de publicaciones diferenciadas en cuatro pestañas por el estado en que se encuentran, ya que se considera que una publicación puede estar en "Reprogramar" (cuando la fecha de aparición se ha vencido o quedó obsoleta), "Pendiente" (cuando la fecha de aparición esta prevista para una fecha mayor a la actual), "Publicada" (cuando se corroboró que fue publicada en alguna edición) o "Cancelada".

.. image:: img/publicacionesdiario.png
   :width: 750 px

En el caso de Publicaciones Diario, además de todos los avisos que se vendieron en Efectivo y Cuenta Corriente, se encuentra en estado “Reprogramar” el aviso especial Centímetros (derivado de la venta por Cuenta Corriente de centimetros), el cual se puede modificar ingresando al formulario y eligiendo la opción “Diseñar” que provee un asistente similar al del módulo ventas, que permite usar esos centimetros disponibles en algun aviso que tenga “cm” como unidad de medida.

.. image:: img/cms.png
   :width: 750 px

Cabe destacar que se puede crear una publicacion que se asocie a una edicion desde esta funcionalidad, pero se debe tener en cuenta que no registrará ventas ni facturas, por lo cual se recomienda usar el Asistente de Venta descripto anteriormente para que asigne adecuadamente las publicaciones en el estado correspondiente.

.. image:: img/altapubldiario.png
   :width: 750 px

Este módulo posee además dos tipos de reportes, uno para guía de avisos comerciales y otro para guía de avisos clasificados en formato .odt.

Publicaciones Radio
"""""""""""""""""""

Las Publicaciones Radio son similares a las de diario solo que mas genéricas ya que se consideran como productos que corresponden a un programa específico que ya tiene definida la cantidad de menciones, categorizadas por Costo Provincial, Costo Nacional o Costo Oficial, que son asociadas a una Edicion (como fecha de aparición)

.. image:: img/altapublradio.png
   :width: 750 px

Se debe tener en cuenta que por las mismas razones que las explicadas en Publicaciones Diario es conveniente el uso del Asistente de Venta.


Publicaciones Digital
"""""""""""""""""""""

Las Publicaciones Digital corresponden a la colocación de Banners publicitarios en una página web, que al igual que en radio se categorizan por Costo Provincial, Costo Nacional y Costo Oficial, y a diferencia del resto se pueden asignar multiples Ediciones (o fechas), ya que generalmente abarcan un período de tiempo de aparición.

.. image:: img/altapubldigital.png
   :width: 750 px

Al igual que lo detallado en Publicaciones Diario no se recomienda realizar publicaciones por fuera del Asistente de Venta.

Suscripción
-----------

.. image:: img/suscripcion.png
   :width: 750 px


El módulo Suscripción consta de las suscripciones de clientes al diario.El cual brinda un asistente que permite definir un periodo de suscripción. 
Cada suscripción consta de entregas las cuales pueden estar en "Pendiente", "Entregada" o "Pagada". El estado de una suscripción “Pagada” se da cuando se registra el pago de un período. Para lo cual se provee la visualización de las facturas asociadas para generar y realizar los pagos de las mismas en la pestaña Ventas del formulario de alta o modificación de suscripción.

.. image:: img/altasuscripcion.png
   :width: 750 px


