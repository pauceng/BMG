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
| A| RST||
| B| RXY||
| C| 000| HALT makine durduran komut|