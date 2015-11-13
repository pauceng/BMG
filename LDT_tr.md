|Op-Code | Operand  |Description|
|----:|:----:|---------|
| 1| RXY| **R** saklayıcısına **XY** bellek gözünde bulunan içeriği **YÜKLE**(LOAD)|
| 2| RXY| **R** saklayıcısına **XY**'ni **YÜKLE**(LOAD)|
| 3| RXY| **R** saklayıcısına **XY** bellek gözünde bulunan içeriği **DEPOLA**(STORE)|
| 4| 0RS| **R** saklayıcısın bit deseninin içeriğini **S** saklayıcısının bit desenine **TAŞI**(MOVE) |
| 5| RST| **S** saklayıcısın içeriği ile **T** saklayıcısının içeriğini topla **R** saklayıcısına **EKLE**(ADD)|
| 6| RST| **S** ve **T** saklayıcılarının bit desenlerinin kayan noktalı notasyon sonucunu R saklayıcısına  **EKLE**(ADD)|
| 7| RST| **S** ve **T** saklayıcılarının bit desenlerinin **OR**(OR kapısı) sonucunu R saklayıcısına  **EKLE**(ADD)|
| 8| RST| **S** ve **T** saklayıcılarının bit desenlerinin **AND**(AND kapısı) sonucunu R saklayıcısına  **EKLE**(ADD)|
| 9| RST| **S** ve **T** saklayıcılarının bit desenlerinin **EXOR**(EXOR kapısı) sonucunu R saklayıcısına  **EKLE**(ADD)|
| A| R0X| **R** saklayıcısın içeriğini **X**bit sağa ROTATE et(dairesel olarak)|
| B| RXY| **R** saklayıcısın içeriğini **0** saklayıcısın içeriğine eşit ise **XY** adresine git değilse **ATLA**|
| C| 000| HALT makine durduran komut|

## Tabloyu anlayışlı yapmak için bazı örnekler;

|address|content|
|:-----:|:-----:|
|00 	| 11	|
|01 	| 0A	|
|02 	| 24	|
|03 	| 04	|
|04 	| B4	|
|05 	| 0A	|
|06 	| 33	|
|07 	| 00	|
|08 	| C0	|
|09 	| 00	|
|0A 	| C0	|
|0B 	| 00	|
|0C 	| C0	|


### Op-Code 1 için;

Örenek kod; 110A

**R1 <- M(0A)**  XY adresinde bulanan içeriği **R1** saklayıcısına yükle, yukardakı adres içerik tablosundan **0A** adresinin gösterdiği içeriği saklayıcıya yükle.

### Op-Code 2 için;

Örenek kod; 2404

**R4 <- '04'**  XY içeriğini **R4** saklayıcısına yükle,

### Op-Code B için

Örenek kod; B40A

**R4** saklayıcısı ile **R0**(Op-Code tablo da belirtilen bir durum her zaman R0 saklayıcısıyla karşılaştırılır) saklayıcılarının içeriğine bak içerik eşit ise XY kısmında gösterilen adrese git yani **0A** adresine git, eşit değilse bu adımı atla devam et. **R4 ve R0** saklayıcılarının eşit olduğunu varsayalım ve XY adresine yani **0A** adresine gidelim. *address content* tablosunu incelersek **0A** adresinde **C0** var bu durumda ise makine sonlanacak demektir(C0 HALT komutudur makineyi durdurur.)

#### Örnek kod için anlaşılması gereken durum 

|Op-Code|Register(R)|X|Y|
|:---:|:---:|:----:|:---:|
|2 	  |	4   |     0|	4|
|B 	  |	4   |     0|	A|