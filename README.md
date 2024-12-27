
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Proyecciones Geográficas en R

<!-- badges: start -->
<!-- badges: end -->

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
  que se este mapeando y el propósito de tu mapa.
- Siempre considerar las distorsiones que cada proyección puede
  introducir en tu mapa.

## Proyecciones 🌍

En el siguiente script se muestra de manera general la estructura del
uso de los diferentes tipos de proyecciones geográficas.

**Enlace:**
<https://dvillasanao.github.io/Proyecciones_SHP/Output/Pojection_CRS.html>
