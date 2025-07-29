# Seguimiento 1
## 1. a  Describa los campos que se encontrará en este tipo de archivos. ¿Qué información está allí contenida? Proporcione ejemplos.

### Campo 1: Identificador de secuencia (seqid)

Corresponde al nombre de la secuencia sobre la que se anotan las características y se identifican las secuencias.

**Ejemplo:**
ctg123 o KK082935.1

### Campo 2: Fuente de la anotación (source)

Describe el algoritmo, software o base de datos que generó la anotación.

**Ejemplo:**
Genbank o . cuando no se especifica la fuente

### Campo 3: Tipo de característica o feature (type)

Define el tipo de elemento biológico anotado, como gen, ARN mensajero, entre otros.

**Ejemplo:**
gene, exon, CDS, TF_binding_site

### Campo 4 y 5. Coordenadas (4:start y 5:end)

Indican la posición inicial y final del elemento sobre la secuencia. Son números enteros positivos, indexados desde 1 (no desde 0).

**Ejemplo:**
1200	8700 (la secuencia se ubica desde la posición 1200 a 8700)

### Campo 6. Puntaje (score)

Valor numérico (p. ej., p-value) asociado a la anotación, indica la calidad o significancia estadística de esta. Si no aplica, se coloca un punto (.).

**Ejemplo:**
6.2e-45 

### Campo 7. Dirección de la hebra (strand)

Indica en qué hebra se encuentra la anotación.
(+) para hebra directa
(-) para hebra inversa
(.) si no aplica

  **Ejemplo:** +

### 8. Fase de lectura (phase: solo para CDS)

Especifica cómo deben agruparse los nucleótidos en codones. Solo es válida para features tipo CDS (Coding DNA Sequence),. Los valores posibles son:

* 0: codón inicia en el primer nucleótido
* 1: codón inicia en el segundo nucleótido
* 2: codón inicia en el tercero nucleótido

**Ejemplo:**
1


### Campo 9.  Atributos adicionales (attributes)

Contiene metadatos en el formato clave=valor, separados por punto y coma. Este campo permite expresar relaciones jerárquicas y nombres visibles. Los atributos mas comunes son:
* *ID*: identificador único del elemento
* *Name*: nombre legible
* *Parent*: indica jerarquía (por ejemplo, un exon puede tener como Parent un mRNA)
* *Alias*: nombre alternativo o identificador secundario
* *Is_circular*: indica si el feature está en una molécula circular (ej. plásmido).
* *Target*: describe el objetivo de una alineación (ej. de proteína a nucleótido).
* *Dbxref*: referencia cruzada a otras bases de datos externas (DB:Accession).


**Ejemplo:**

ID=gene00001;Name=EDEN

---

### Ejemplo completo de una línea GFF3

```
KK082935.1   ensembl   CDS   1050   1200   .   +   0   ID=cds:ENSCDS00001234;Parent=transcripto:ENST00005678;Name=EDEN-001
```

Esta línea indica que:
* El identificador de la secuencia es KK082935.1 (campo 1)
* La fuente de la anotación es ensembl (campo 2)
* Se trata de una región de ADN que se traduce en proteína: CDS (campo 3)
* Ubicado entre las posiciones 1050 y 1200 (campos 4 y 5)
* No hay valor de score (campo 6)
* En la hebra positiva (campo 7)
* Phase = 0, el primer nucleótido de esta región inicia un codón completo (campo 8)
* Con identificador único del CDS ID=cds:ENSCDS00001234, el CDS pertenece al transcritpgene00001 y su nombre visible es *EDEN-001*  (campo 9)

---

## 3. a.  Proporcione una breve descripción del organismo asignado
La tortuga pintada occidental cuyo nombre científico actual es *Chrysemys picta bellii* con NCBI Taxonomy ID 8478, tiene un cariotipo diploide de 25 cromosomas y según el NIH, su genoma posee 25.344 genes que codifican proteínas (70.8%), 6.980 genes no codificantes (19.5%), 2.239 genesde small RNAs (6.3%) y 1.155 pseudogenes (3.2%), siendo en total 35.718 genes

<img width="696" height="342" alt="image" src="https://github.com/user-attachments/assets/139ea0f6-881b-450d-a17c-062daa2dbebe" />

**Figura 1.** Fotografía del organismo *Chrysemys picta bellii*. **Tomada de:** Encyclopedia of Life (s.f.).

**Referencias**

National Center for Biotechnology Information. (s.f.). *Chrysemys picta bellii*. NCBI Taxonomy. U.S. National Library of Medicine. https://www.ncbi.nlm.nih.gov/datasets/taxonomy/8478/

Encyclopedia of Life. (s.f.). Western painted turtle (*Chrysemys picta bellii*). EOL. https://eol.org/pages/10991094 

---
## 3. b. i.  ¿Cuantos features contiene el archivo?
El archivo contiene 9 categorías y **1243114** features o anotaciones biológicas descritas cada una en una fila de datos.

---

## 3. b. ii. ¿Cuantas regiones de la secuencia (cromosomas) contiene el archivo?
En el archivo, las líneas que comienzan con **##sequence-region** indican que se describe la región de una secuencia seguida de seqid, start y end de la misma. Estas regiones son un metadato, mas no una anotación biológica como tal, donde se puede contar el número de cromosomas. Según el NCBI, el organismo tiene 25 pares de cromosomas, sin embargo, al contar las regiones, se encuentran  en el genoma **78.595** regiones. Esto es debido a que al reconstruir la secuencia completa de ADN de un organismo se generan ensamblajes genómicos jerárquicos: primero se generan contigs a partir de secuencias individuales, que luego se unen en scaffolds, y finalmente, si existe suficiente información de mapeo, los scaffolds se ensamblan en cromosomas. En muchos genomas, el ensamblaje solo llega hasta el nivel de scaffold, por lo que cada uno de ellos aparece también como una ##sequence-region en el GFF3, por ende, hay múltiples regiones de secuencia en este organismo (Ensembl GRCh37, 2025). 

*Nota:* Además, los scaffolds pueden ser placed (ubicados en un cromosoma), unlocalised (pertenecen a un cromosoma pero sin posición u orientación definida) o unplaced (no se sabe a qué cromosoma pertenecen) (Ensembl GRCh37, 2025).

**Referencia**

Ensembl GRCh37 (2025). *Chromosomes, scaffolds and contigs*. https://grch37.ensembl.org/info/genome/genebuild/chromosomes_scaffolds_contigs.html#:~:text=The%20shortest%20assembly%20components%20are%20contigs%2C%20which%20are,have%20only%20been%20assembled%20to%20the%20scaffold%20level.

---

## 3. b. iii. ¿Cuántos genes están listados en el organismo?
Según el tipo de feature, hay **26827** genes listados en el organismo.

---

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


