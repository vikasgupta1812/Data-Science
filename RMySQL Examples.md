RMySQL
========================================================



```r
library(RMySQL)
```

```
## Loading required package: DBI
```



```r
ucscDb <- dbConnect(MySQL(), user = "genome", host = "genome-mysql.cse.ucsc.edu")
result <- dbGetQuery(ucscDb, "show databases;")
dbDisconnect(ucscDb)
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
## 17           bosTauMd3
## 18             braFlo1
## 19             caeJap1
## 20              caePb1
## 21              caePb2
## 22             caeRem2
## 23             caeRem3
## 24             calJac1
## 25             calJac3
## 26             canFam1
## 27             canFam2
## 28             canFam3
## 29             cavPor3
## 30                 cb1
## 31                 cb3
## 32                ce10
## 33                 ce2
## 34                 ce4
## 35                 ce6
## 36             cerSim1
## 37             choHof1
## 38             chrPic1
## 39                 ci1
## 40                 ci2
## 41             danRer1
## 42             danRer2
## 43             danRer3
## 44             danRer4
## 45             danRer5
## 46             danRer6
## 47             danRer7
## 48             dasNov3
## 49             dipOrd1
## 50                 dm1
## 51                 dm2
## 52                 dm3
## 53                 dp2
## 54                 dp3
## 55             droAna1
## 56             droAna2
## 57             droEre1
## 58             droGri1
## 59             droMoj1
## 60             droMoj2
## 61             droPer1
## 62             droSec1
## 63             droSim1
## 64             droVir1
## 65             droVir2
## 66             droYak1
## 67             droYak2
## 68             echTel1
## 69             echTel2
## 70             equCab1
## 71             equCab2
## 72             eriEur1
## 73             felCat3
## 74             felCat4
## 75             felCat5
## 76                 fr1
## 77                 fr2
## 78                 fr3
## 79             gadMor1
## 80             galGal2
## 81             galGal3
## 82             galGal4
## 83             gasAcu1
## 84             geoFor1
## 85                  go
## 86            go080130
## 87            go140213
## 88             gorGor3
## 89             hetGla1
## 90             hetGla2
## 91                hg16
## 92                hg17
## 93                hg18
## 94                hg19
## 95         hg19Patch10
## 96          hg19Patch2
## 97          hg19Patch5
## 98          hg19Patch9
## 99                hg38
## 100            hgFixed
## 101             hgTemp
## 102          hgcentral
## 103            latCha1
## 104            loxAfr3
## 105            macEug1
## 106            macEug2
## 107            melGal1
## 108            melUnd1
## 109            micMur1
## 110               mm10
## 111         mm10Patch1
## 112                mm5
## 113                mm6
## 114                mm7
## 115                mm8
## 116                mm9
## 117            monDom1
## 118            monDom4
## 119            monDom5
## 120            musFur1
## 121            myoLuc2
## 122            nomLeu1
## 123            nomLeu2
## 124            nomLeu3
## 125            ochPri2
## 126            oreNil1
## 127            oreNil2
## 128            ornAna1
## 129            oryCun2
## 130            oryLat2
## 131            otoGar3
## 132            oviAri1
## 133            oviAri3
## 134            panTro1
## 135            panTro2
## 136            panTro3
## 137            panTro4
## 138            papAnu2
## 139            papHam1
## 140 performance_schema
## 141            petMar1
## 142            petMar2
## 143            ponAbe2
## 144            priPac1
## 145            proCap1
## 146     proteins120806
## 147     proteins121210
## 148     proteins140122
## 149           proteome
## 150            pteVam1
## 151            rheMac1
## 152            rheMac2
## 153            rheMac3
## 154                rn3
## 155                rn4
## 156                rn5
## 157            sacCer1
## 158            sacCer2
## 159            sacCer3
## 160            saiBol1
## 161            sarHar1
## 162            sorAra1
## 163           sp120323
## 164           sp121210
## 165           sp140122
## 166            speTri2
## 167            strPur1
## 168            strPur2
## 169            susScr2
## 170            susScr3
## 171            taeGut1
## 172            tarSyr1
## 173               test
## 174            tetNig1
## 175            tetNig2
## 176            triMan1
## 177            tupBel1
## 178            turTru2
## 179            uniProt
## 180            vicPac1
## 181            vicPac2
## 182           visiGene
## 183            xenTro1
## 184            xenTro2
## 185            xenTro3
```




```r
hg19 <- dbConnect(MySQL(), user = "genome", db = "hg19", host = "genome-mysql.cse.ucsc.edu")
allTables <- dbListTables(hg19)
length(allTables)
```

```
## [1] 10993
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
affyMis <- fetch(query)
quantile(affyMis$misMatches)
```

```
##   0%  25%  50%  75% 100% 
##    1    1    2    2    3
```






```r
affyMisSmall <- fetch(query, n = 10)
dbClearResult(query)
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


