# Proyectos-Power-BI
# 馃搳 **Proyectos realizados en Power BI** 馃搳

馃搱 Proyecto 01 - Ventas historicas de videojuegos.
[Enlace a dashboard](https://app.powerbi.com/view?r=eyJrIjoiYjkyYTY1YWQtZDlhNC00YWJkLTgyMDAtYzkyN2QxNjk1OTUzIiwidCI6IjQ3YWU4MzQxLTE4YjQtNDM3NC04YzU5LTQ3NDc4ZjIxZjdhYSJ9)

馃搱 Proyecto 02 (Parte 1) - Analis铆s de la poblaci贸n por continente y pa铆s. [Enlace a dashboard](https://app.powerbi.com/view?r=eyJrIjoiZGQzNTU4M2YtNzgzNC00NGI0LWFjNWEtYWFlZDk3ZDE1OGJjIiwidCI6IjQ3YWU4MzQxLTE4YjQtNDM3NC04YzU5LTQ3NDc4ZjIxZjdhYSJ9)

馃搲 Proyecto 02 (Parte 2) - Analis铆s de mortalidad y esperanza de vida por regiones. [Enlace a dashboard](https://app.powerbi.com/view?r=eyJrIjoiZGQzNTU4M2YtNzgzNC00NGI0LWFjNWEtYWFlZDk3ZDE1OGJjIiwidCI6IjQ3YWU4MzQxLTE4YjQtNDM3NC04YzU5LTQ3NDc4ZjIxZjdhYSJ9)

馃搱 Proyecto 03 - Reporte de RRHH (Analisis de sueldos y Evaluaci贸n de Desempe帽o). [Enlace a dashboard](https://app.powerbi.com/view?r=eyJrIjoiNjgyMDBiMWYtNWY4YS00OTUxLWE4ODItN2E4Yjc2OGM1MjUyIiwidCI6IjQ3YWU4MzQxLTE4YjQtNDM3NC04YzU5LTQ3NDc4ZjIxZjdhYSJ9&pageName=ReportSection)

馃搱 Proyecto 04 - Finanzas Personales (Ingresos, Gastos, Utilidad, Saldo).
[Enlace a dashboard](https://app.powerbi.com/view?r=eyJrIjoiZTEzMDM1MzctOTliZi00OTdhLTlmMWEtYzQ3NTEwYjJjNTRmIiwidCI6IjQ3YWU4MzQxLTE4YjQtNDM3NC04YzU5LTQ3NDc4ZjIxZjdhYSJ9&pageName=ReportSection)

馃搱 Proyecto 05 - Proyecto DAX. 
[Enlace a dashboard](https://app.powerbi.com/view?r=eyJrIjoiZWIwYjY2OGMtMDE4Ny00MGUxLWI4MjItNzk3OGJjMzQwZWY1IiwidCI6IjQ3YWU4MzQxLTE4YjQtNDM3NC04YzU5LTQ3NDc4ZjIxZjdhYSJ9&pageName=ReportSection9834bed03828d8011034)

#

# 馃憖 **Algunos Tips para Power BI** 馃憖

	Atajos   

**Alt + Enter  o  Shift + Enter** = Salto a un nuevo rengl贸n

**Tab** = Indentaci贸n o autocompletado de c贸digo (intellisense)

**//** = Agregar Comentarios

**Alt + 鈫戔啌** = Mover un rengl贸n

**Shift + Alt** + 鈫戔啌** = Copiar un rengl贸n

**Alt + Click** = Selecciones multiples

**Ctrl + Scroll Mouse** = Zoom expresi贸n DAX

**Click en par茅ntesis** = Resalta (Highlight) donde termina funci贸n

**Ctrl + F2  o  Ctrl + Shift + L**  =  Cambiar multiples veces la misma tabla/columna/medida

**Shift + ?** = Lista de atajos de teclado de Power BI Desktop

#

	Columnas   
  
## M贸dulo: Funciones de Fecha y Tiempo

A帽o = YEAR(DimCalendar[DateKey])

Mes = MONTH(DimCalendar[DateKey])

Dia = DAY(DimCalendar[DateKey])

Trimestre = QUARTER(DimCalendar[DateKey])

SemanaA帽o = WEEKNUM(DimCalendar[DateKey],2)

Dia Semana = WEEKDAY(DimCalendar[DateKey],2)

DiasPromo = DATEDIFF(DimPromotion[StartDate], DimPromotion[EndDate], DAY)

## M贸dulo: Funciones Condicionales y L贸gicas

Cantidad Total = FactSales[SalesQuantity] - FactSales[ReturnQuantity]

Devolucion = IF(FactSales[ReturnQuantity]>0,"Si","No")

Tipo Venta = IF(FactSales[SalesQuantity]>10,"Mayoreo","Menudeo")

Tipo Devolucion = IF(FactSales[ReturnQuantity]=0,BLANK(),IF(FactSales[ReturnQuantity]=1,"Unica","Multiple"))

Fin Semana = IF( NOT DimCalendar[DiaSemana] in {1,2,3,4,5} ,"Fin de Semana", "D铆a Laboral")

Mala Suerte = IF((DimCalendar[CalendarDayOfWeekLabel]="Tuesday" || DimCalendar[CalendarDayOfWeekLabel]="Friday") && DimCalendar[Dia]=13,"Mala Suerte", "D铆a Normal")

Dcto Mayoreo = IF(FactSales[TipoVenta] = "Mayoreo" && FactSales[channelKey] = 1 && FactSales[PromotionKey] = 1,0.05,0)

## M贸dulo: Funciones de Texto

Ubicaci贸n Completa = DimGeography[RegionCountryName] & ", " & DimGeography[ContinentName]

Trimestre = "Trimestre " & QUARTER(DimCalendar[DateKey])

Mes Corto = LEFT(DimCalendar[CalendarMonthLabel],1)

Mes Txt = FORMAT(DimCalendar[DateKey], "MMMM")

Dia Txt = FORMAT(DimCalendar[DateKey], "DDDD")

FS = UPPER(DimCalendar[Fin Semana])

FS = LOWER(DimCalendar[Fin Semana])

Tienda = SUBSTITUTE(DimStores[StoreName], "Store", BLANK())

## M贸dulo: Funci贸n RELATED

Ubicacion Fisica = IF(DimStores[StoreType]="Store", DimStores[Ciudad] & ", " & RELATED(DimGeography[Ubicaci贸n Completa]), BLANK())

Precio Unitario = RELATED(DimProduct[UnitPrice])

Ingresos = FactSales[Precio Unitario] * FactSales[CantidadTotal]

#

	Medidas     	

## M贸dulo: Funciones matem谩ticas y estad铆sticas

Cantidad Ventas = SUM(FactSales[SalesQuantity])

Cantidad Devoluciones = SUM(FactSales[ReturnQuantity])

Cantidad Total = [Cantidad Ventas] - [Cantidad Devoluciones]

Ratio Devoluciones = DIVIDE([Cantidad Devoluciones],[Cantidad Ventas],0)

Ratio Devoluciones = 鈥淟a cantidad de devoluciones respecto a ventas es: 鈥? & DIVIDE([Cantidad Devoluciones],[Cantidad Ventas],0)

PU Promedio = AVERAGE(DimProduct[UnitPrice])

Cantidad Tiendas = COUNT(DimStores[StoreKey])

Cantidad Tiendas = COUNTA(DimStores[StoreKey])

Cantidad Tiendas = COUNTROWS(DimStores)

Cantidad Tiendas con Ventas = DISTINCTCOUNT(DimStores[StoreKey])

Cantidad Regiones = COUNTA(DimGeography[RegionCountryName])

Cantidad Regiones 2 = COUNTROWS(DimGeography)

Cantidad Regiones en Blanco = COUNTBLANK(DimGeography[RegionCountryName])

Cantidad Regiones Unicas = DISTINCTCOUNT(DimGeography[RegionCountryName])

Total Ordenes = COUNTROWS(FactSales)

## M贸dulo: Funci贸n CALCULATE

Total Ordenes Devueltas = CALCULATE([Total Ordenes], FactSales[ReturnQuantity] > 0)

Total Ordenes Devueltas Multiples = CALCULATE([Total Ordenes], FactSales[ReturnQuantity] > 0, FactSales[TipoDevolucion] = "Multiple")

## M贸dulo: Funci贸n ALL / FILTER

ALL Total Ordenes = CALCULATE([Total Ordenes],ALL(FactSales))

% Ordenes Devueltas = DIVIDE([Total Ordenes Devueltas],[ALL Total Ordenes])

PU Promedio General = CALCULATE([PU Promedio], ALL(DimProduct))

Total Ordenes Devueltas Multiples FILTER = CALCULATE([Total Ordenes], FILTER(FactSales, FactSales[ReturnQuantity] > 0), FILTER(FactSales, FactSales[TipoDevolucion] = "Multiple"))

Total Ordenes PU Alto = CALCULATE([Total Ordenes], FILTER(DimProduct, DimProduct[UnitPrice] > [PU Promedio General]))

## M贸dulo: Funci贸n SUMX

Total Ingresos X = SUMX(FactSales, FactSales[CantidadTotal] * RELATED(DimProduct[UnitPrice]))

## M贸dulo: Funciones de Time Intelligence

YTD Ingresos = CALCULATE([Total Ingresos], DATESYTD(DimCalendar[DateKey]))

YTD Ingresos 2 = TOTALYTD([Total Ingresos],DimCalendar[DateKey])

MTD Ingresos = TOTALMTD([Total Ingresos],DimCalendar[DateKey])

## M贸dulo: Funciones de Variaci贸n

Total Ingresos LY = CALCULATE([Total Ingresos], SAMEPERIODLASTYEAR(DimCalendar[DateKey]))

Total Ingresos Variacion LY = [TotalIngresos] - [Total Ingresos LY]

Total Ingresos Variacion LM = CALCULATE([Total Ingresos], DATEADD(DimCalendar[DateKey],-1,MONTH))

## M贸dulo: Modificando Medidas

Descuento = IF(FactSales[TipoVenta] = "Mayoreo" && FactSales[channelKey] = 1 && FactSales[PromotionKey] = 1,0.05,RELATED(DimPromotion[DiscountPercent]))

Total Ingresos = SUMX(FactSales, FactSales[CantidadTotal] * RELATED(DimProduct[UnitPrice]) * (1 - FactSales[Descuento]))

// Total Ingresos es la cantidad de piezas multiplicado por el precio unitario y por el descuento aplicado

Total Ingresos Sin Dcto = SUMX(FactSales, FactSales[CantidadTotal] * RELATED(DimProduct[UnitPrice]))

## M贸dulo: Funci贸n RANKX

Rank Ingresos Tiendas = IF( ISBLANK([Total Ingresos]) , BLANK(), RANKX(ALL(DimStores), [Total Ingresos]))

Rank Ingresos Tiendas Seleccionadas = IF( ISBLANK([Total Ingresos]) , BLANK(), RANKX(ALLSELECTED(DimStores), [Total Ingresos]))

Rank Ingresos SubCatProductos = IF( ISBLANK([Total Ingresos]) , BLANK(), RANKX(ALL(DimProductSubcategory), [Total Ingresos]))

Rank Ingresos SubCatProductos Seleccionados = IF( ISBLANK([Total Ingresos]) , BLANK(), RANKX(ALLSELECTED(DimProductSubcategory), [Total Ingresos]))

## M贸dulo: Funci贸n SWITCH

Categoria Tama帽o Tienda = SWITCH( TRUE(),

DimStores[SellingAreaSize] <= 500, "Peque帽a",

DimStores[SellingAreaSize] <= 800, "Mediana",

DimStores[SellingAreaSize] > 800, "Grande",

"Otro")

---------------------

Rank Ingresos Tiendas Cat = 

IF(HASONEVALUE(DimStores[Tienda]),

SWITCH( TRUE(),

[Rank Ingresos Tiendas] <= 10 , "Top 10",

[Rank Ingresos Tiendas] <= 25 , "Sobresaliente",

[Rank Ingresos Tiendas] <= 50 , "Bueno",

[Rank Ingresos Tiendas] <= 100 , "Regular",

"Incompetente") , BLANK()

)

---------------------

Star Unichar = 

VAR star = UNICHAR(9733)

VAR star0 = UNICHAR(9734)

RETURN

REPT(star, 4) & star0

---------------------

Rank Ingresos Tiendas Cat Unichar = 

VAR star = "猸愶笍"

VAR star0 = UNICHAR(9734)

RETURN

IF(HASONEVALUE(DimStores[Tienda]),

SWITCH( TRUE(),

[Rank Ingresos Tiendas] <= 10 , REPT(star,5),

[Rank Ingresos Tiendas] <= 25 , REPT(star,4) & REPT(star0,1),

[Rank Ingresos Tiendas] <= 50 , REPT(star,3) & REPT(star0,2),

[Rank Ingresos Tiendas] <= 100 , REPT(star,2) & REPT(star0,3),

REPT(star,1) & REPT(star0,4)) , BLANK()

)

--------------------

## M贸dulo: Selector con SWITCH

Total Costos = SUMX(FactSales, FactSales[Cantidad Total] * RELATED(DimProduct[UnitCost]))

Total Utilidad = [Total Ingresos] - [Total Costos]

---------------------

Total Selecci贸n = 

IF(ISCROSSFILTERED(Selector[Selecci贸n]),

SWITCH(TRUE(),

VALUES(Selector[Selecci贸n]) = "Total Ingresos", [Total Ingresos],

VALUES(Selector[Selecci贸n]) = "Total Costos", [Total Costos],

VALUES(Selector[Selecci贸n]) = "Total Utilidad", [Total Utilidad],

[Total Ingresos]),

[Total Ingresos])

---------------------









