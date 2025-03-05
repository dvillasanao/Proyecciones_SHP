
<!-- README.md is generated from README.Rmd. Please edit that file -->

# 🌍 Proyecciones Geográficas en R

<!-- badges: start -->
<!-- badges: end -->

Las proyecciones geográficas son fundamentales para visualizar y
analizar datos espaciales con precisión. En este repositorio, explora el
manejo y la transformación de proyecciones geográficas en R utilizando
paquetes especializados como `sf`, `ggplot2` y `rnaturalearth`.

<div style="display: flex; justify-content: center;">

<img src="Output/World Geodetic System 1984.png" width="55%" style="margin: 1px;">
<img src="Output/Peirce Q projection.png" width="45%" style="margin: 1px;">

</div>

## 📦 Paquetes Utilizados

``` r
library(sf)
library(ggplot2)
library(rnaturalearth)
```

## Tipos de Proyecciones y Cuándo Usarlas

- **1. Proyección Mercator (EPSG:3857)**: Útil para mapas web globales,
  aunque distorsiona las áreas en latitudes altas.

``` r
st_transform(data, crs = 3857)
```

- **2. Proyección Lambert Conformal Conic**: Adecuada para mapear áreas
  de latitud media.

``` r
st_transform(data, crs = "+proj=lcc +lat_1=33 +lat_2=45 +lat_0=39 +lon_0=-96")
```

- **3. Proyección Albers Equal Area**: Ideal para representar áreas
  grandes manteniendo proporciones correctas.

``` r
st_transform(data, crs = "+proj=aea +lat_1=29.5 +lat_2=45.5 +lat_0=37.5 +lon_0=-96")
```

- **4. Proyección UTM (Universal Transverse Mercator)**: Buena para
  mapear áreas más pequeñas con alta precisión.

``` r
st_transform(data, crs = 32619)  # UTM zone 19N
```

## Ejemplo de Uso

``` r
# Cargar datos del mundo
world <- ne_countries(scale = "medium", returnclass = "sf")

# Crear mapa con proyección Mercator
ggplot() +
  geom_sf(data = st_transform(world, 3857)) +
  ggtitle("Mapa Mundial - Proyección Mercator")
```

## Notas Importantes

- La elección de la proyección dependerá del área geográfica específica
  que se este mapeando y el propósito del mapa.
- Siempre considerando las distorsiones que cada proyección puede
  introducir en tu mapa.

## Proyecciones 🌍

En el siguiente script se muestra de manera general la estructura del
uso de los diferentes tipos de proyecciones geográficas.

**Enlace:**
<https://dvillasanao.github.io/Proyecciones_SHP/Output/Pojection_CRS.html>

## Código de Conducta

Por favor, revisa el [Código de Conducta](CODE_OF_CONDUCT.md) antes de
contribuir.

## Licencia

Este trabajo de Diana Villasana Ocampo está bajo una
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/">
Licencia Creative Commons Atribución 4.0 Internacional.</a>.
