|Op-Code | Operand  |Description|
|----:|:----:|---------|
| 1| RXY| **R** saklayıcısına **XY** bellek gözünde bulunan içeriği **YÜKLE**(LOAD)|
| 2| RXY| **R** saklayıcısına **XY**'yi **YÜKLE**(LOAD)|
| 3| RXY| **R** saklayıcısının içeriğini **XY** bellek gözüne **DEPOLA**(STORE)|
| 4| 0RS| **R** saklayıcısın bit deseninin içeriğini **S** saklayıcısının bit desenine **TAŞI**(MOVE) |
| 5| RST| **S** saklayıcısın içeriği ile **T** saklayıcısının içeriğini topla **R** saklayıcısına **EKLE**(ADD)|
| 6| RST| **S** ve **T** saklayıcılarının bit desenlerinin kayan noktalı notasyon sonucunu R saklayıcısına  **EKLE**(ADD)|
| 7| RST| **S** ve **T** saklayıcılarının bit desenlerinin **OR**(OR kapısı) sonucunu R saklayıcısına  **EKLE**(ADD)|
| 8| RST| **S** ve **T** saklayıcılarının bit desenlerinin **AND**(AND kapısı) sonucunu R saklayıcısına  **EKLE**(ADD)|
| 9| RST| **S** ve **T** saklayıcılarının bit desenlerinin **EXOR**(EXOR kapısı) sonucunu R saklayıcısına  **EKLE**(ADD)|
| A| R0X| **R** saklayıcısının içeriğinin ikilik tabanda gösterimini(8 bit'e tamamlayarak) **X** kere sağa **ROTATE** et(dairesel olarak)|
| B| RXY| **R** saklayıcısının içeriği **0** saklayıcısının içeriğine eşit ise **XY** adresine git değilse bu adımı **ATLA**|
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

### Op-Code 1 için;

Örenek kod; 110A

**XY** adresinde bulanan içeriği **R1** saklayıcısına yükle, yukardakı adres içerik tablosundan **0A** adresinin gösterdiği içeriği saklayıcıya yükle. Yani, *address content* tablosu incelediğimiz zaman **XY** adresimizin içeriği **C0** 'rı R1 saklayıcısna yükleyecektir.

**R1** <-- **M(0A)**  

### Op-Code 2 için;

Örenek kod; 2404

**XY** içeriğini **R4** saklayıcısına yükle,

**R4** <-- **'04'**

### Op-Code B için

Örenek kod; B40A

**R4** saklayıcısı ile **R0**(*Op-Code tablo da belirtilen bir durum her zaman R0 saklayıcısıyla karşılaştırılır*) saklayıcılarının içeriğine bak içerik eşit ise XY adresine git yani, **0A** adresine git, eşit değilse bu adımı atla devam et. **R4 ve R0** saklayıcılarının eşit olduğunu varsayalım ve XY adresine, yani **0A** adresine gidelim. *address content* tablosunu incelersek **0A** adresinde **C0** var bu durumda ise makine sonlanacak demektir(C0 HALT komutudur makineyi durdurur.)

### Op-Code A için;

Örnek kod; A203

**R** saklayıcısın içeriğini **X**bit sağa ROTATE et;

**NOT:** Bu adımda dikkat edilmesi gereken ilk nokta LDT tablosunda **A** Op-Code için Operand **R0X** .Yapmamız gereken ne? X kadar ROTATE et, yani XY gibi düşünürsek **Y** 'nin yerinde duran kısım bize lazım. R2 saklayıcısnın içeriğini 3 bit sağa ROTATE etmemiz gerekiyor.

#### Örnek kod için anlaşılması gereken durum 

Örnek|Op-Code |Saklayıcı(R)|X|Y|
-----|:------:|:---:|:----:|:---:|
110A |1 	  |	1   |     0|	A|
2404 |2 	  |	4   |     0|	4|
A203 |A 	  |	2   |     0|	3|
B40A |B 	  |	4   |     0|	A|


---------
### BMG(Bilgisayar Mühendisliğine Giriş) 2014 final sorusu çözümü

|address|content|	|address|content|
|:-----:|:-----:|---|:-----:|:-----:|
|00 	| 25	|	|07 	| 00	|
|01 	| 03	|	|08 	| 34	|
|02 	| A5	|	|09 	| 04	|
|03 	| 02	|	|0A 	| B0	|
|04 	| 35	|	|0B 	| 03	|
|05 	| 03	|	|0C 	| C0	|
|06 	| 24	|	|0D 	| 00	|


* **Öndeclikle içerikleri(content) ikili grup şeklinde gruplar haline getirelim**

Op-Code | R | X | Y |
-------:|---|---|---|
  	  2 | 5 | 0 | 3 |
  	  A | 5 | 0 | 2 |
  	  3 | 5 | 0 | 3 |
  	  2 | 4 | 0 | 0 |
  	  3 | 4 | 0 | 4 |
  	  B | 0 | 0 | 3 |
  	  C | 0 | 0 | 0 |

![](https://github.com/PAU-Projects/BMG/blob/master/img/img1.png)
![](https://github.com/PAU-Projects/BMG/blob/master/img/img2.png)
![](https://github.com/PAU-Projects/BMG/blob/master/img/img3.png)

----
Sorunun çözümü - [pdf](https://github.com/PAU-Projects/BMG/raw/master/doc/tr/BilgisayarMuhendisligineGirisFinalSoru.pdf)
