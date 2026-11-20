# Consultas para vendedores

## 1. Encontrar la referencia oficial

> Usá Mercado Libre DevSite para buscar «órdenes ventas orders/search vendedor» en español de Argentina (MLA). Mostrame la referencia oficial para gestionar órdenes.

**Resultado observado en ChatGPT Work.** La herramienta de búsqueda devolvió «Órdenes», en la categoría «Gestionar ventas», y sugirió leer la ruta `gestiona-ventas`.

## 2. Identificar los requisitos de la API

> Abrí la página «Órdenes» de Mercado Libre DevSite. Indicame el endpoint de búsqueda, el filtro por vendedor, cómo filtrar órdenes pagadas y cómo navegar la paginación. Citá la página y distinguí los campos requeridos de los opcionales.

Contrastá la respuesta con la [referencia oficial](https://developers.mercadolibre.com.ar/es_ar/gestiona-ventas). Este paso consulta documentación.

## 3. Verificar una orden real desde una integración autorizada

En una terminal local, con un token válido para la API de órdenes y el ID numérico de tu propia cuenta vendedora cargados en `ML_ACCESS_TOKEN` y `ML_SELLER_ID`:

```bash
: "${ML_ACCESS_TOKEN:?Cargá un token de acceso para la API de Mercado Libre}"
: "${ML_SELLER_ID:?Cargá el ID de tu cuenta vendedora}"

curl --fail-with-body --silent --show-error --get \
  'https://api.mercadolibre.com/orders/search' \
  --header "Authorization: Bearer ${ML_ACCESS_TOKEN}" \
  --data-urlencode "seller=${ML_SELLER_ID}" \
  --data-urlencode 'order.status=paid'
```

Esta llamada es un ejemplo basado en la documentación y queda pendiente de prueba con una cuenta vendedora. En una prueba exitosa, revisá `results` y `paging`. Una lista vacía puede ser válida si no hay órdenes que coincidan. Si documentás tu resultado, registrá la fecha, el país y si la consulta fue exitosa. Mantené el token y las respuestas con datos de compradores fuera del repositorio.
