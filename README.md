# NFTs-Market-Place-Server

Introduccion.

NFTs Market Place, es un espacio para que los usuario puedan comprar y vender NFTs. Pudiendo crear una cunta de usuario que les permita la compra y la venta de los activos digitales.

1.El usuario

1.1 Creando un usuario (register)
Usted podrá crear un usuario para la compra y venta de NFTs, pero esto no limita su acceso a ver los NFTs disponibles y las categorias que albergan estos mismos.
Para la creacion del ususario, será necesario enviar por el body, un json con la los siguientes campos del modelo user: {username, email, password}

1.2 Token de sesion activa (login)
Una vez que haya creado su usuario, deberá registrarse y pasarle al body {email y password} para que le se otorgado un token único y poder navegar mientres no haya expirado dicho token. Este token deberá ser colocado en Authorization y buscar el tipo de token "BEARER" despues colocarlo en el input correspondiente. \*nota: cada que inicie sesion con otro usuario o haya caducado el token deberá repetir dicho paso.

1.3 Actualizar y elimiar mi cuenta (patch)
Unicamente este acción podrá ser llevada a cabo con un usuario existente. Para eso vamos a mandar por el body ( en el caso de actualizar ) los campos a actualizar, y por el params, osea por la url o endpoint ,el id propio del usuario. ejemplo: http://localhost:4020/api/v1/users/1, y no enviar nada por ningun canal, solamente enviar la peticion delete. Para este último solamente debará arrojar un 204 y un status exitoso.

1.4 traer mis tickes o ordenes de compra
Para esta acción se debera primero hacer una compra de un carrito de NFTs. De lo contrario, deberá aparecer el error 404 de que aún no tienes compras.

2.NFTs

2.1 creando un NFT
Para esta acción primero se deben de crear las categorias. Una vez creadas las categoria entoes de debe pasar todos los valores a traves de form-data unicamente, ya que tambien se mandan imágenes y form-data es el único que las puede cagar a traves de streaming. Para subir la imagen a los valores, se debera hacer hover en el input de Key y seleccionar tipo file y en value de este, se deberá cargar la imagen desde nuestro computador. Los valores que deberan ser pasados son: title, description, price, categoryId, quantiy, nftImg (la o las imagenes, se podrán como máximo 5)

2.2 ver todos o uno de los NFTs y Categorias
Como ya se ha mencionado, ver uno o todos los NFTs no se requerira tner una sesion iniciada y activa. Simplemente mandando la peticion get o introduciendo el id al final de la url colocada (ejemplo: "/1") que son los params, nos servira para traer con exito nuestra peticion.

2.3 actualizar o eliminar NFT
Para esta acción unicamente el dueño del NFT creado podrá realizar dichas acciones. Para llevar acabo las mismas, se debera segur los mismos pasas que para los de usuario.

2.4 categorias
las categoias solamnte se les debe enviar un valor por el body en un json, {name}

2.5 actualizar o eliminar categorias
De la misma forma que para usuarios y NFTs, se deberá tener una sesion activa y solo el dueño de la misma podrá hacer dichas acciones.

3.El carrito

3.1 subiendo productos al carrito
Para subir un producto al carrito, se deberá pasar por el body en un json, el
{nftId, quantity}. Si ya esta el producto, no se podrá volver a subir.

3.2 actualizando y eliminedo del carrito
Para esta acción será necesario enviar por el body un json con la cantidad a actualizar unicament {quantity}. En el caso de elimianr del carrit, no se deberá enviar nada, solo enviar la peticion con el id dinámico en la url al final.

3.3 comprando el carrito
para comprar el carrito solamente se deberá enviar la peticion post y nada mas. El mesaje de regreso es un status exitoso. Depués de esta acción ya se podrán visualizar las ordens o tickets del usuario.
