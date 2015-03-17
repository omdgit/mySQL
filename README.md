# Readme
omdgit  
March 16, 2015  

This is the Readme file with some basic R scripts for interacting with mySQL.  The scripts are from the Coursera course **Getting and Cleaning Data**. 


```r
library(RMySQL)
```

```
## Loading required package: DBI
```

```r
ucscDb <- dbConnect(MySQL(), user = "genome", host = "genome-mysql.cse.ucsc.edu")
result <- dbGetQuery(ucscDb, "show databases;"); dbDisconnect(ucscDb);
```

```
## [1] TRUE
```

```r
result
```

```
##               Database
## 1   information_schema
## 2              ailMel1
## 3              allMis1
## 4              anoCar1
## 5              anoCar2
## 6              anoGam1
## 7              apiMel1
## 8              apiMel2
## 9              aplCal1
## 10             balAcu1
## 11             bosTau2
## 12             bosTau3
## 13             bosTau4
## 14             bosTau5
## 15             bosTau6
## 16             bosTau7
## 17             bosTau8
## 18           bosTauMd3
## 19             braFlo1
## 20             caeJap1
## 21              caePb1
## 22              caePb2
## 23             caeRem2
## 24             caeRem3
## 25             calJac1
## 26             calJac3
## 27             calMil1
## 28             canFam1
## 29             canFam2
## 30             canFam3
## 31             cavPor3
## 32                 cb1
## 33                 cb3
## 34                ce10
## 35                 ce2
## 36                 ce4
## 37                 ce6
## 38             cerSim1
## 39             choHof1
## 40             chrPic1
## 41                 ci1
## 42                 ci2
## 43             criGri1
## 44             danRer1
## 45             danRer2
## 46             danRer3
## 47             danRer4
## 48             danRer5
## 49             danRer6
## 50             danRer7
## 51             dasNov3
## 52             dipOrd1
## 53                 dm1
## 54                 dm2
## 55                 dm3
## 56                 dm6
## 57                 dp2
## 58                 dp3
## 59             droAna1
## 60             droAna2
## 61             droEre1
## 62             droGri1
## 63             droMoj1
## 64             droMoj2
## 65             droPer1
## 66             droSec1
## 67             droSim1
## 68             droVir1
## 69             droVir2
## 70             droYak1
## 71             droYak2
## 72             eboVir3
## 73             echTel1
## 74             echTel2
## 75             equCab1
## 76             equCab2
## 77             eriEur1
## 78             eriEur2
## 79             felCat3
## 80             felCat4
## 81             felCat5
## 82                 fr1
## 83                 fr2
## 84                 fr3
## 85             gadMor1
## 86             galGal2
## 87             galGal3
## 88             galGal4
## 89             gasAcu1
## 90             geoFor1
## 91                  go
## 92            go080130
## 93            go140213
## 94            go150121
## 95             gorGor3
## 96             hetGla1
## 97             hetGla2
## 98                hg16
## 99                hg17
## 100               hg18
## 101               hg19
## 102        hg19Patch10
## 103         hg19Patch2
## 104         hg19Patch5
## 105         hg19Patch9
## 106               hg38
## 107         hg38Patch2
## 108            hgFixed
## 109             hgTemp
## 110          hgcentral
## 111            latCha1
## 112            loxAfr3
## 113            macEug1
## 114            macEug2
## 115            melGal1
## 116            melUnd1
## 117            micMur1
## 118               mm10
## 119         mm10Patch1
## 120                mm5
## 121                mm6
## 122                mm7
## 123                mm8
## 124                mm9
## 125            monDom1
## 126            monDom4
## 127            monDom5
## 128            musFur1
## 129            myoLuc2
## 130            nomLeu1
## 131            nomLeu2
## 132            nomLeu3
## 133            ochPri2
## 134            ochPri3
## 135            oreNil1
## 136            oreNil2
## 137            ornAna1
## 138            oryCun2
## 139            oryLat2
## 140            otoGar3
## 141            oviAri1
## 142            oviAri3
## 143            panTro1
## 144            panTro2
## 145            panTro3
## 146            panTro4
## 147            papAnu2
## 148            papHam1
## 149 performance_schema
## 150            petMar1
## 151            petMar2
## 152            ponAbe2
## 153            priPac1
## 154            proCap1
## 155     proteins120806
## 156     proteins121210
## 157     proteins140122
## 158           proteome
## 159            pteVam1
## 160            rheMac1
## 161            rheMac2
## 162            rheMac3
## 163                rn3
## 164                rn4
## 165                rn5
## 166                rn6
## 167            sacCer1
## 168            sacCer2
## 169            sacCer3
## 170            saiBol1
## 171            sarHar1
## 172            sorAra1
## 173            sorAra2
## 174           sp120323
## 175           sp121210
## 176           sp140122
## 177            speTri2
## 178            strPur1
## 179            strPur2
## 180            susScr2
## 181            susScr3
## 182            taeGut1
## 183            taeGut2
## 184            tarSyr1
## 185               test
## 186            tetNig1
## 187            tetNig2
## 188            triMan1
## 189            tupBel1
## 190            turTru2
## 191            uniProt
## 192            vicPac1
## 193            vicPac2
## 194           visiGene
## 195            xenTro1
## 196            xenTro2
## 197            xenTro3
```

```r
hg19 <- dbConnect(MySQL(), user = "genome", db = "hg19", host = "genome-mysql.cse.ucsc.edu")
allTables <- dbListTables(hg19)
length(allTables)
```

```
## [1] 11012
```

```r
allTables[1:5]
```

```
## [1] "HInv"         "HInvGeneMrna" "acembly"      "acemblyClass"
## [5] "acemblyPep"
```

```r
dbListFields(hg19, "affyU133Plus2")
```

```
##  [1] "bin"         "matches"     "misMatches"  "repMatches"  "nCount"     
##  [6] "qNumInsert"  "qBaseInsert" "tNumInsert"  "tBaseInsert" "strand"     
## [11] "qName"       "qSize"       "qStart"      "qEnd"        "tName"      
## [16] "tSize"       "tStart"      "tEnd"        "blockCount"  "blockSizes" 
## [21] "qStarts"     "tStarts"
```

```r
dbGetQuery(hg19, "select count(*) from affyU133Plus2")
```

```
##   count(*)
## 1    58463
```

```r
affyData <- dbReadTable(hg19, "affyU133Plus2")
```

```
## Warning: Unsigned INTEGER in col 0 imported as numeric
## Warning: Unsigned INTEGER in col 1 imported as numeric
## Warning: Unsigned INTEGER in col 2 imported as numeric
## Warning: Unsigned INTEGER in col 3 imported as numeric
## Warning: Unsigned INTEGER in col 4 imported as numeric
## Warning: Unsigned INTEGER in col 5 imported as numeric
## Warning: Unsigned INTEGER in col 6 imported as numeric
## Warning: Unsigned INTEGER in col 7 imported as numeric
## Warning: Unsigned INTEGER in col 8 imported as numeric
## Warning: Unsigned INTEGER in col 11 imported as numeric
## Warning: Unsigned INTEGER in col 12 imported as numeric
## Warning: Unsigned INTEGER in col 13 imported as numeric
## Warning: Unsigned INTEGER in col 15 imported as numeric
## Warning: Unsigned INTEGER in col 16 imported as numeric
## Warning: Unsigned INTEGER in col 17 imported as numeric
## Warning: Unsigned INTEGER in col 18 imported as numeric
```

```r
head(affyData)
```

```
##   bin matches misMatches repMatches nCount qNumInsert qBaseInsert
## 1 585     530          4          0     23          3          41
## 2 585    3355         17          0    109          9          67
## 3 585    4156         14          0     83         16          18
## 4 585    4667          9          0     68         21          42
## 5 585    5180         14          0    167         10          38
## 6 585     468          5          0     14          0           0
##   tNumInsert tBaseInsert strand        qName qSize qStart qEnd tName
## 1          3         898      -  225995_x_at   637      5  603  chr1
## 2          9       11621      -  225035_x_at  3635      0 3548  chr1
## 3          2          93      -  226340_x_at  4318      3 4274  chr1
## 4          3        5743      - 1557034_s_at  4834     48 4834  chr1
## 5          1          29      -    231811_at  5399      0 5399  chr1
## 6          0           0      -    236841_at   487      0  487  chr1
##       tSize tStart  tEnd blockCount
## 1 249250621  14361 15816          5
## 2 249250621  14381 29483         17
## 3 249250621  14399 18745         18
## 4 249250621  14406 24893         23
## 5 249250621  19688 25078         11
## 6 249250621  27542 28029          1
##                                                                   blockSizes
## 1                                                          93,144,229,70,21,
## 2              73,375,71,165,303,360,198,661,201,1,260,250,74,73,98,155,163,
## 3                 690,10,32,33,376,4,5,15,5,11,7,41,277,859,141,51,443,1253,
## 4 99,352,286,24,49,14,6,5,8,149,14,44,98,12,10,355,837,59,8,1500,133,624,58,
## 5                                       131,26,1300,6,4,11,4,7,358,3359,155,
## 6                                                                       487,
##                                                                                                  qStarts
## 1                                                                                    34,132,278,541,611,
## 2                        87,165,540,647,818,1123,1484,1682,2343,2545,2546,2808,3058,3133,3206,3317,3472,
## 3                   44,735,746,779,813,1190,1195,1201,1217,1223,1235,1243,1285,1564,2423,2565,2617,3062,
## 4 0,99,452,739,764,814,829,836,842,851,1001,1016,1061,1160,1173,1184,1540,2381,2441,2450,3951,4103,4728,
## 5                                                     0,132,159,1460,1467,1472,1484,1489,1497,1856,5244,
## 6                                                                                                     0,
##                                                                                                                                      tStarts
## 1                                                                                                             14361,14454,14599,14968,15795,
## 2                                     14381,14454,14969,15075,15240,15543,15903,16104,16853,17054,17232,17492,17914,17988,18267,24736,29320,
## 3                               14399,15089,15099,15131,15164,15540,15544,15549,15564,15569,15580,15587,15628,15906,16857,16998,17049,17492,
## 4 14406,20227,20579,20865,20889,20938,20952,20958,20963,20971,21120,21134,21178,21276,21288,21298,21653,22492,22551,22559,24059,24211,24835,
## 5                                                                         19688,19819,19845,21145,21151,21155,21166,21170,21177,21535,24923,
## 6                                                                                                                                     27542,
```

```r
query <- dbSendQuery(hg19, "select * from affyU133Plus2 where misMatches between 1 and 3")
```

```
## Warning: Unsigned INTEGER in col 0 imported as numeric
## Warning: Unsigned INTEGER in col 1 imported as numeric
## Warning: Unsigned INTEGER in col 2 imported as numeric
## Warning: Unsigned INTEGER in col 3 imported as numeric
## Warning: Unsigned INTEGER in col 4 imported as numeric
## Warning: Unsigned INTEGER in col 5 imported as numeric
## Warning: Unsigned INTEGER in col 6 imported as numeric
## Warning: Unsigned INTEGER in col 7 imported as numeric
## Warning: Unsigned INTEGER in col 8 imported as numeric
## Warning: Unsigned INTEGER in col 11 imported as numeric
## Warning: Unsigned INTEGER in col 12 imported as numeric
## Warning: Unsigned INTEGER in col 13 imported as numeric
## Warning: Unsigned INTEGER in col 15 imported as numeric
## Warning: Unsigned INTEGER in col 16 imported as numeric
## Warning: Unsigned INTEGER in col 17 imported as numeric
## Warning: Unsigned INTEGER in col 18 imported as numeric
```

```r
affyMis <- fetch(query); quantile(affyMis$misMatches)
```

```
##   0%  25%  50%  75% 100% 
##    1    1    2    2    3
```

```r
affyMisSmall <- fetch(query, n=10); dbClearResult(query);
```

```
## [1] TRUE
```

```r
dim(affyMisSmall)
```

```
## [1] 10 22
```

```r
dbDisconnect(hg19)
```

```
## [1] TRUE
```
