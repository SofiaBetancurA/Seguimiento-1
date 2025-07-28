# Seguimiento 1
## 1. a  Describa los campos que se encontrará en este tipo de archivos. ¿Qué información está allí contenida? Proporcione ejemplos.

### Campo 1: Identificador de secuencia (seqid)

Corresponde al nombre de la secuencia sobre la que se anotan las características.
**Ejemplo:**
ctg123

### Campo 2: Fuente de la anotación (source)

Describe el algoritmo, software o base de datos que generó la anotación.
**Ejemplo:**
Genbank o . cuando no se especifica la fuente

### Campo 3: Tipo de característica o feature (type)

Define el tipo de elemento biológico anotado, como gen, ARN mensajero, entre otros. Debe estar basado en el **Sequence Ontology (SO)**.
**Ejemplo:**
gene, mRNA, CDS, TF_binding_site

### Campo 4 y 5. Coordenadas (4:start y 5:end)

Indican la posición inicial y final del elemento sobre la secuencia. Son números **enteros positivos**, indexados desde 1 (no desde 0 como en otros formatos).
**Ejemplo:**
1200	8700 (la secuencia se ubica desde la posición 1200 a 8700)

### Campo 6. Puntaje (score)

Valor numérico (p. ej., e-value o p-value) asociado a la anotación. Si no aplica, se coloca un punto (`.`).
**Ejemplo:**
6.2e-45 

### Campo 7. Dirección de la hebra (strand)

Indica en qué hebra se encuentra la anotación.

* `+` para hebra directa
* `-` para hebra inversa
* `.` si no aplica
  **Ejemplo:**
+

### 8. Fase de lectura (phase: solo para CDS)

Especifica cómo deben agruparse los nucleótidos en codones. Solo es válida para features tipo `CDS`. Los valores posibles son:

* `0`: codón inicia en el primer nucleótido
* `1`: codón inicia en el segundo nucleótido
* `2`: codón inicia en el tercero nucleótido

**Ejemplo:**
1


### Campo 9.  Atributos adicionales (attributes)

Contiene metadatos en el formato `clave=valor`, separados por punto y coma. Este campo permite expresar relaciones jerárquicas y nombres visibles. Los atributos mas comunes son:
* `ID`: identificador único del elemento
* `Name`: nombre legible
* `Parent`: indica jerarquía (por ejemplo, un `exon` puede tener como `Parent` un `mRNA`)
* `Alias`, `Note`, `Dbxref`, entre otros.

**Ejemplo:**

ID=gene00001;Name=EDEN

---

### Ejemplo completo de una línea GFF3

```txt
ctg123 genbank gene 1000 9000 . + . ID=gene00001;Name=EDEN
```

Esta línea indica que:
* El identificador de la secuencia es ctg123 (campo 1)
* Se extrajo de una base de datos (campo 2)
* Se trata de un gen (campo 3)
* Ubicado entre las posiciones 1000 y 9000 (campos 4 y 5)
* En la hebra positiva (campo 7)
* Con ID único `gene00001` y nombre visible `EDEN` (campo 9)

---

## 3. a.  Proporcione una breve descripción del organismo asignado



## 3. b. i.  ¿Cuantos features contiene el archivo?
El archivo contiene 9 categorías y 1243114 features o anotaciones biológicas descritas cada una en una fila de datos.


## 3. b. ii. ¿Cuantas regiones de la secuencia (cromosomas) contiene el archivo?



## 3. b. iii. ¿Cuántos genes están listados en el organismo?
Según el tipo de feature, hay 26827 genes listados en el organismo.


## 3. b. iii. ¿Cuál es el top 10 de tipo de features (columna 3) más anotados en el genoma?
Organizados de mayor a menor, los primeros 10 tipos de feature que mas se repiten, junto con la cantidad de veces que se encuentra anotado en el genoma son: 
487284  exon
461131  CDS
93323   biological_region
78595   region
39074   mRNA
31069   five_prime_UTR
21186   gene
18665   three_prime_UTR
5523    ncRNA_gene
4314    lnc_RNA


