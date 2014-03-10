Para hacer uso de la libreria solo basta con instanciar la clase asi:

require_once 'edPDF/edpdf.php';
$edpdf = new edPDF();

luego puede hacer uso de las funciones directamente de edPDF o de fpdf.

.::::::::::::::::::::DOCUMENTACION::::::::::::::::::::.

/**
* public function edPdfAddPage(@params)
* Funcion para agregar paginas del documento al documento generado
* 
* @param String $documento => Nombre de la plantilla
* @param Int $pagina => Pagina de la plantilla que desea importar en la nueva pagina del documento
* @param String $ruta => Ruta en donde se encuentran alojadas las plantillas en el servidor (Default => uploads/plantillas/)
*/


/**
* public function insertar(@params);
* Funcion para insertar el texto deseado en la plantilla PDF
* 
* @param String $texto => Texto a insertar
* @param Int $x => Posicion en X
* @param Int $y => Posicion en Y
* @param String $style => Estilo de la letra puede usar BUI (siendo B => Negrita, U => subrayado, I => Italica)
* @param Int $font_size => Tamaño de la fuente
* @param String $family => Font family
*/


/**
* public function insertarCelda(@params);
* Funcion para insertar el texto deseado en la plantilla PDF
* a traves de un MultiCell
* 
* @param String $texto => Texto a insertar
* @param Int $x => Posicion en X
* @param Int $y => Posicion en Y
* @param Int $w => Ancho de celdas. Si 0, estos se extienden hasta l márgen derecha de la página.
* @param Int $h => Alto de las celdas
* @param String $a => Alineacion del texto puede usar LCRJ (Siendo L = izquierda, C= centrado, R = derecha, J = texto justificado [por defecto]) 
* @param String $style => Estilo de la letra puede usar BUI (siendo B => Negrita, U => subrayado, I => Italica)
* @param Int $font_size => Tamaño de la fuente
* @param Boolean
* @param String $family => Font family
*/


/**
* public function generarPDF(@params);
* Exportar PDF
* 
* @param String $nombre_documento => Nombre de la salida del documento
* @param Char $destino => Destino de salida valores opcionales de fpdf (pueden ser I => ver en navegador, D => forzar descarga)
*/


/**
* public function edPdfAddAllPages(@params);
* Funcion para descargar el documento (plantilla) en vacio en caso que se requira
* 
* @param String $documento => Nombre del documento con Extension (.pdf)
* @param String $ruta => Ruta de la carpeta que contiene las plantillas (Default = uploads/plantillas/)
*/


/**
* public function asignarColor(@params);
* Convertir de Hexadecimal a RGB
* 
* @param String/Array $hex => Color en formato hexadecimal
*/


/**
* public function asignarFondo(@params);
* Convertir de Hexadecimal a RGB
* 
* @param String/Array $hex => Color en formato hexadecimal
*/


ejemplo de uso:

<?php
	require_once 'edPDF/edpdf.php';
	$edpdf = new edPDF();
	
	$edpdf->edPdfAddPage('miplantilla.pdf', 1); //en donde el primer
						    parametro es la ruta 
						    de la plantilla pdf, 
						    y el segundo parametro 
						    es la pagina que desea
						    importar desde la plantilla.
						    
	$this->edpdf->insertar("Texto que desea insertar", 14, 49, 'BIU', 26); //('texto', posicionX, posicionY, 'Estilo', tamaño_fuente);
	
	$this->edpdf->generarPDF('NombrePDF_Salida.pdf', 'I'); //I para ver en navegador, D para descarga
	
	/** Tambien puede usar insertarCell con los parametros ya explicados lo que automaticamente
 	    dara saltos de linea a textos muy largos.
	**/	
	