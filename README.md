<div align="center">
<h1>Mercado Libre MCP</h1>
<p><strong>Guía de integración para ChatGPT Work y Codex</strong></p>
<p><a href="https://www.daraforce.com/">DARA FORCE</a> · OpenAI Partner Network</p>
<p><em>We make it happen.</em></p>
</div>

---

Esta guía independiente muestra cómo conectar el MCP oficial de Mercado Libre DevSite, consultar su documentación técnica y encontrar el camino para recuperar órdenes de una cuenta vendedora.

Guía desarrollada por [Dara Force](https://www.daraforce.com/), empresa argentina de ingeniería e integración de inteligencia artificial.

## ChatGPT Work

1. En ChatGPT web, abrí **Complementos** y elegí **+ → Add custom MCP server**.
2. Usá **Mercado Libre DevSite** como nombre y pegá esta URL:

   ```text
   https://mcp.mercadolibre.com/devsite/v1/mcp
   ```

3. Seleccioná **OAuth** y completá la autorización con tu cuenta de Mercado Libre. Guardá la conexión como complemento siguiendo las opciones que muestre la interfaz.
4. En Work, seleccioná el complemento y probá el primer ejemplo de [consultas para vendedores](examples/ventas-seller.md).

[Documentación de ChatGPT para agregar un MCP personalizado](https://developers.openai.com/api/docs/guides/custom-mcp-server)

## Codex

Agregá el bloque de [codex.config.toml](examples/codex.config.toml) a tu archivo `~/.codex/config.toml`. Conservá el resto de tu configuración. Desde la terminal:

```bash
codex mcp list
codex mcp login mercadolibre-devsite
```

Completá OAuth en el navegador, abrí una sesión de Codex y ejecutá la misma consulta de prueba. La lista de servidores comprueba la configuración. Una respuesta de la herramienta de búsqueda comprueba la conexión.

[Documentación oficial de Mercado Libre DevSite MCP](https://developers.mercadolibre.com.ar/es_ar/autenticacion-y-autorizacion/mcp-server)

## Recuperar las ventas de un seller

| Paso | Resultado esperado | Estado |
| --- | --- | --- |
| Buscar cómo consultar órdenes del vendedor | Referencia oficial a la página «Órdenes» | Verificado con la herramienta de búsqueda del MCP en ChatGPT Work |
| Leer filtros y autenticación de órdenes | Requisitos de `GET /orders/search` según la referencia oficial | Revisado en la documentación |
| Obtener órdenes de una cuenta real | Respuesta de la API con las órdenes autorizadas | Pendiente de prueba con una cuenta vendedora |
| Conectar una instalación nueva en Work o Codex | OAuth completo y primera consulta exitosa | Pasos documentados, pendientes de prueba de extremo a extremo |

El MCP DevSite documenta herramientas de búsqueda y lectura de documentación. La recuperación efectiva de ventas se hace mediante la **API de órdenes de Mercado Libre** y requiere un token de acceso autorizado para esa llamada. El OAuth del complemento autoriza la conexión con el MCP.

[Ejemplos y protocolo de prueba](examples/ventas-seller.md) · [Referencia oficial de órdenes](https://developers.mercadolibre.com.ar/es_ar/gestiona-ventas)

## Licencia

Los archivos de esta guía se distribuyen bajo [licencia MIT](LICENSE). El servidor, la API y las marcas pertenecen a sus respectivos titulares.

[Dara Force](https://www.daraforce.com/) · [Leonardo Condorí](https://leocondori.com/)
