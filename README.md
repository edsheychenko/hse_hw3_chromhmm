# hse_hw3_chromhmm

# Ссылка на колаб:
https://colab.research.google.com/drive/1NYuJw1AjMOemUY_660uQyU9YpEPwSb0a?usp=sharing

# Исходные данные
Клеточная линия:GM12878
## Table1
Клеточная линия | Гистоновая метка | Имя файла | Файл с контролем 
| --- | --- | --- | ---
GM12878|H2azStd|H2azStd.bam|Control.bam
GM12878|H3k4me1Std|H3k4me1Std.bam|Control.bam
GM12878|H3k4me3Std|H3k4me3Std.bam|Control.bam
GM12878|H3k4me2Std|H3k4me2Std.bam|Control.bam
GM12878|H3k9acStd|H3k9acStd.bam|Control.bam
GM12878|H3k9me3Std|H3k9me3Std.bam|Control.bam
GM12878|H3k27acStd|H3k27acStd.bam|Control.bam
GM12878|H3k27me3Std|H3k27me3Std.bam|Control.bam
GM12878|H3k36me3Std|H3k36me3Std.bam|Control.bam
GM12878|H3k79me2Std|H3k79me2Std.bam|Control.bam
GM12878|H4k20me1Std|H4k20me1Std.bam|Control.bam

# Выдача после ChromHMM
|![emissions_10](https://user-images.githubusercontent.com/93148512/160274344-6d3c9a05-40c1-44ea-98b9-0596d4a8c79d.png)| ![transitions_10](https://user-images.githubusercontent.com/93148512/160274357-a3bc71b6-3d04-4fd2-854d-81f379b30a96.png) | ![GM12878_10_overlap](https://user-images.githubusercontent.com/93148512/160274468-de25274a-6431-4f06-bbfb-126be4210fee.png) | ![GM12878_10_RefSeqTSS_neighborhood](https://user-images.githubusercontent.com/93148512/160274483-3a3883e1-cd30-4a7b-9318-c11f046eb1ca.png)|![GM12878_10_RefSeqTES_neighborhood](https://user-images.githubusercontent.com/93148512/160274490-390f8eb6-836f-488e-ae66-0f8f0190f92b.png)|
| ------------- | ------------- |--------------------| -- | -- |

# Биологическая роль гистоновых меток
|Метка|Имя файла|Роль|
|:--|--|--:|
|H2az|H2azStdAlnRep1.bam|Ключевой регулятор хроматиновой сигнализации|
|H3k4me1|H3k4me1StdAlnRep1.bam|Ассоциируется с энхансерами (gene enhancers)|
|H3k4me3|H3k4me3StdAlnRep1.bam|Связана с активацией транскрипции близлежащих генов, связана с промоторами|
|H3k4me2|H3k4me2StdAlnRep1.bam|Ассоциирована с активацией генов|
|H3k9ac|HH3k9acStdAlnRep1.bam|Является частью активного состояния промотора|
|H3k9me3|H3k9me3StdAlnRep1.bam|Указывает на 3-метелирование, ассоциирована с гетерохроматином|
|H3k27ac|H3k27acStdAlnRep1.bam|Связан с более высокой активацией транскрипции и поэтому определяется как активный энхансер.|
|H3k27me3|H3k27me3StdAlnRep1.bam|Формирование гетерохроматических областей и понижением регуляции близлежащих генов (downregulation).|
|H3k36me3|H3k36me3StdAlnRep1.bam|Связана с телами генов,также может быть вовлечена в определение экзонов.|
|H3k79me2|H3k79me2StdAlnRep1.bam|Маркер неактивных областей хроматина.|
|H4k20me1|H4k20me1StdAlnRep1.bam|Связана с активацией транскрипции.|

На основании выдачи ChromHMM, геномного браузера и литературы были получены примерные названия эпигенетических типов:

|Состояние|1|2|3|4|5|6|7|8|9|10|
|--|--|--|--|--|--|--|--|--|--|--|
|Метки|H3k4me1, немного H2az|H3k4me1,H3k4me2,H3k27ac, немного H2az,H3k9ac,H3k4me3|H3k4me2,H2az,H3k4me3,немного H3k9ac|H3k4me2,H2az,H3k9ac,H3k27ac,H3k4me3,H3k79me2|H3k4me1,H3k4me2,H3k79me2,H3k4me3,H3k27ac,немного H3k9ac|H3k79me2, немного H3k36me3|немного H3k36me3|-|H3k4me3,H3k27ac,H3k27me3,H3k9me3, немного H3k36me3|H3k27me3|
|Часть генома|конец транскрицпии, ядерная ламина, гены, экзоны|конец транскрицпии, ядерная ламина, гены, экзоны|CpG island, экзоны,начало транскрицпии, конец транскрипции|CpG island, экзоны,начало транскрицпии, конец транскрипции, гены|гены, конец транскрицпии,экзоны|гены| экзоны, гены, конец транскрицпии| много в геноме, ядерная ламина|ядерная ламина, конец транскрипции|ядерная ламина, конец транскрипции|
|Расположение относительно TSS(старт транскрипции)|немного до старта|-|до старта, далее спад после старта|растёт до старта, после старта максимум, а потом на спад|немного до и в конце TSS|-|-|-|немног на самом старте|-|
|Расположение относительно TES(конец транскрипции)|равномерно распределено до и после|постепенно возрастает|много до начала, а после TES идёт на спад|много до TES, потом идёт на спад и еще есть в конце|равномерно распределено|-|ярко выражено до начала, немного уменьшается ближе к концу|-|немного до, чуть больше на и после|распределено равномерно|
|Итог|Active promoter|Active promoter|Strong Enhancer|Enhancer|Enhancer|Transcribed region|Heterochromatin|Heterochromatin|Polycomb-repressed|Weak promoter|
