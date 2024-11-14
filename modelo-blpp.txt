////////////////////////////////////////////////////////////////////////////////
//
// MODELO DE PAQUETES HTTP/JSON PARA INTERFAZ BLiPiP (RED MODULAR Y RECURSIVA) <
// codigo: json, txt, commonmark, html, svg, css, ecmascript, wasm, base64, blob

[ /* <-- matriz global */
[ /* <-- lista local */

/* [0] METADATOS */
{
  indice_gl: "num", // indice en matriz global
  nombre_ls: "txt", // titulo lista (ls) local
  i_persona: "web", // pag^interfaz modo de uso (ui, texto, prompt, canvas, etc)
  s_botones: "obj", // arbol^sistema api para integracion de boton en comentario
  s_archivo: "obj", // ls^sistema de archivos {indice_loc: nombre_loc.extension}
  l_secuenc: ["num", ..."num"], // ls^inidice nodo anterior /.?/ y siguiente(es)
  // l_secuenc primer num es "null" en inicio gl. siguientes nums son opcionales
  l_finales: ["num", ..."num"], // ls^inidice finales (segun de orden aparicion)
  // l_finales es "null" si lista actual es final de un camino (lista de listas)
},

/* [1] ARCHIVO BASICO. INDEX */
"texto serializado",

/* [2... -2] ARCHIVOS COMPLEMENTARIOS */
"texto serializado",
"texto serializado", 
"texto serializado", // ...etc

/* [-1] HASH-256 */
"string 64 chars", // genera estructura recursiva
],

// otras listas locales
[],
[],
[], // ...etc
]

////////////////////////////////////////////////////////////////////////////////
/*

Para escribir un paquete:
  1. se crean y relacionan las listas (arboles)
  2. se defina una jerarquia de caminos (finales)
  3. se ordenan las listas en una matriz global.
  4. se genera un identificador unico (UUID)

Para publicar un paquete:
  1. se crea un hash a partir del string (persona + "_" + UUID)
  2. se asigna ese hash al primer indice de la matriz global.
  3. luego, por cada elemento se crea un nuevo hash a partir de:
  (hash anterior + "_" + json de lista actual, sin contar -1).
  4. cada hash se agrega al final de cada lista (en posicion -1)
  5. se crea un json final a partir de la matriz global.

Para edicion interna de un paquete (enlaces azules):
  1. se crea nueva lista como expansion de alguna existente.
  2. por retrocompatibilidad: no se pueden crear nuevos finales.
  3. se genera hash de lista actual (a partir del ultimo hash global)
  4. se inserta json actual al final del json matriz global.
  5. se comenta enlace en nodo de origen (incio lista)
  6. opcional: comentario segun api boton para mejor usabilidad.
  7. los comentarios soportados por la misma persona son azules
  y pasan (tardiamente) a formar parte oficial del paquete.

Para abrir un paquete:
  1. se descarga el paquete completo.
  2. se revierten los hashes, comenzando desde el ultimo.
  3. si todos los hashes concuerdan con el valor del contenido.
  entonces el paquete es valido (es una copia del original).
  4. se transforma matriz en arboles (listas relacionadas).

Para edicion externa de un paquete (enlaces rojos):
  1. se descarga y valida el paquete completo. se abre.
  2. se crea nueva lista como divergencia de alguna existente.
  3. a partir del hash del nodo de divergencia + "_" + lista actual
  se genera nuevo hash y se le incluye en posicion -1.
  4. se publica como json parcial (no matriz) en servidor del
  paquete original, que lo soportará mientras sea convenido.
  5. se comenta enlace en nodo de origen (salida divergente)
  6. opcional: comentario segun api boton para mejor usabilidad.
  7. los comentarios soportados por servidores externos son rojos
  a menos que en algun momento la persona a cargo del soporte
  los incluyan oficialmente en el paquete y pasen a ser azules.
  8. para ser incluidos deben adaptarse a algun final oficial.

Para clonar un paquete:
  1. se descarga y valida el paquete completo. se abre.
  2. se edita libremente. se puede reescribir cualquier cosa.
  3. al terminar se genera un nuevo identificador unico (UUID)
  4. se publica como un paquete independiente, con hashes nuevos.
  5. pueden (o no) incluirse creditos al paquete original y/o
  referencias del nuevo paquete en comentarios del original.

*/
////////////////////////////////////////////////////////////////////////////////

// mj-una. al dominio publico. cc0. no es necesario citar autoria.
// version 0.1 (14 / 11 / 24)
