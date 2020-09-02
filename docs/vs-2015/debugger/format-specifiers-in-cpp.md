---
title: Specifikátory formátu v jazyce C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f620cbf5d522b99965268f35c00ff8e874f1542
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834165"
---
# <a name="format-specifiers-in-c"></a>Specifikátory formátu v jazyce C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit formát, ve kterém se hodnota zobrazuje v okně **kukátka** , pomocí specifikátorů formátu.  
  
 Můžete také použít specifikátory formátu v **příkazovém** okně, v **příkazovém** okně a dokonce i ve zdrojových oknech. Pokud v těchto oknech pozastavíte výraz, výsledek se zobrazí v DataTip. Zobrazení DataTip odráží specifikátor formátu.  
  
> [!NOTE]
> Nativní ladicí program sady Visual Studio se změnil na nový ladicí stroj. V rámci této změny byly přidány některé nové specifikátory formátu a některé staré byly odebrány. Starší ladicí program se pořád používá, když provedete spolupráci (smíšené nativní a spravované) ladění s využitím C++/CLI. Následující části v tomto tématu znázorňují specifikátory formátu pro každý ladicí stroj.  
> 
> - [Specifikátory formátu](#BKMK_Visual_Studio_2012_format_specifiers) popisují specifikátory formátu v novém ladicím modulu.  
>   - [Specifikátory formátu pro spolupráci při ladění pomocí C++/CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) popisuje specifikátory formátu ve starším modulu ladění.  
  
## <a name="using-format-specifiers"></a>Použití specifikátorů formátu  
 Pokud máte následující kód:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Přidejte `my_var1` proměnnou do okna **kukátka** (při ladění, **ladění/Windows/sledování/kukátko 1**) a nastavte zobrazení na šestnáctkové (v okně **kukátko** klikněte pravým tlačítkem myši na proměnnou a vyberte možnost **hexadecimální zobrazení**). Nyní okno Kukátko ukazuje, že obsahuje hodnotu 0x0065. Chcete-li zobrazit tuto hodnotu vyjádřenou jako znak namísto celého čísla, ve sloupci název za názvem proměnné přidejte specifikátor formátu znaku **c**. Sloupec **Value** se teď zobrazuje s **101 "e"**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specifikátory formátu  
 V následujících tabulkách jsou uvedeny specifikátory formátu, které lze použít v aplikaci Visual Studio. Specifikátory tučného písma nejsou podporované pro spolupráci s/CLI. C++.  
  
|Specifikátor|Formát|Původní hodnota kukátka|Zobrazená hodnota|  
|---------------|------------|--------------------------|---------------------|  
|d|desítkové celé číslo|0x00000066|102|  
|o|osmičkové celé číslo bez znaménka|0x00000066|000000000146|  
|x<br /><br /> **y**|šestnáctkové celé číslo|102|0xcccccccc|  
|X<br /><br /> **H**|šestnáctkové celé číslo|102|0xCCCCCCCC|  
|c|jeden znak|0x0065, c|101 "e"|  
|s|const char * řetězec|\<location> Hello World|Hello World|  
|**SB**|const char * řetězec|\<location> Hello World|Ahoj světe|  
|S8|const char * řetězec|\<location> Hello World|Hello World|  
|**s8b**|const char * řetězec|\<location> Hello World|Hello World|  
|Pá|const wchar_t * const<br /><br /> char16_t \* řetězec|\<location> L "Hello World"|L "Hello World"<br /><br /> u "Hello World"|  
|jednotk|const wchar_t * const<br /><br /> char16_t \* řetězec|\<location> L "Hello World"|Ahoj světe|  
|bstr|Řetězec BSTR|\<location> L "Hello World"|L "Hello World"|  
|**s32**|Řetězec UTF-32|\<location> U "Hello World"|U "Hello World"|  
|**s32b**|Řetězec UTF-32 (žádné uvozovky)|\<location> U "Hello World"|Ahoj světe|  
|**otevřít**|enum|Sobota (6)|Sobota|  
|**hv**|Typ ukazatele – určuje, že hodnota kontrolovaného ukazatele je výsledkem přidělení haldy pole, například `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, …}|  
|**ná**|Potlačí adresu paměti ukazatele na objekt.|\<location>, {member = Value...}|{member = Value...}|  
|**c**|Zobrazí pouze informace základní třídy, ignorování odvozených tříd.|`(Shape*) square` zahrnuje základní třídu a informace o odvozených třídách.|Zobrazí jenom informace o základní třídě.|  
|hod|Kód chyby HRESULT nebo Win32. (Ladicí program nyní dekóduje HRESULTs automaticky, takže tento specifikátor není v těchto případech vyžadován.|S_OK|S_OK|  
|wc|Příznak třídy okna|0x0010|WC_DEFAULTCHAR|  
|WM|Čísla zpráv systému Windows|16|WM_CLOSE|  
|!|nezpracovaný formát, který ignoruje přizpůsobení zobrazení datových typů|\<customized representation>|4|  
  
> [!NOTE]
> Když je přítomen specifikátor formátu **HV** , ladicí program se pokusí určit délku vyrovnávací paměti a zobrazit příslušný počet prvků. Protože není vždy možné, aby ladicí program mohl najít přesnou velikost vyrovnávací paměti pole, měli byste použít specifikátor velikosti, kdykoli je `(pBuffer,[bufferSize])` to možné. Specifikátor formátu **HV** je určený pro scénáře, ve kterých není velikost vyrovnávací paměti snadno dostupná.  
  
### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Specifikátory velikosti pro ukazatele jako pole  
 Pokud máte ukazatel na objekt, který chcete zobrazit jako pole, můžete použít celé číslo nebo výraz k určení počtu prvků pole:  
  
|Specifikátor|Formát|Původní Valuen kukátka|Zobrazená hodnota|  
|---------------|------------|---------------------------|---------------------|  
|n|Desítkové nebo **šestnáctkové** celé číslo|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|Zobrazí se `pBuffer` jako pole elementu 32.|  
|**oček**|Platný výraz C++, který je vyhodnocen jako celé číslo.|pBuffer, [bufferSize]|Zobrazí pBuffer jako pole `bufferSize` prvků.|  
|**Rozbalit (n)**|Platný výraz C++, který se vyhodnotí jako celé číslo|pBuffer, expand (2)|Zobrazí třetí prvek  `pBuffer`|  
  
## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Specifikátory formátu pro spolupráci při ladění pomocí C++/CLI  
 Specifikátory **tučným písmem** jsou podporovány pouze pro ladění nativních a C++/CLI kódu.  
  
|Specifikátor|Formát|Původní hodnota kukátka|Zobrazená hodnota|  
|---------------|------------|--------------------------|---------------------|  
|**d, i**|desítkové celé číslo se znaménkem|0xF000F065|-268373915|  
|**h**|desítkové celé číslo bez znaménka|0x0065|101|  
|o|osmičkové celé číslo bez znaménka|0xF065|0170145|  
|x, X|Šestnáctkové celé číslo|61541|0x0000f065|  
|**l, h**|dlouhá nebo krátká předpona pro: d, i, u, o, x, X|00406042|0x0c22|  
|**FJ**|přihlášený plovoucí bod|(3./2.), f|1,500000|  
|**cerebrální**|podepsaný vědecký zápis|(3.0/2.0)|1.500000 e + 000|  
|**věcn**|signed Point nebo signed vědecký zápis, podle toho, co je kratší|(3.0/2.0)|1.5|  
|c|jeden znak|\<location>|101 "e"|  
|s|const char *|\<location>|Hello World|  
|Pá|const wchar_t *<br /><br /> char16_t const\*|\<location>|L "Hello World"|  
|jednotk|const wchar_t *<br /><br /> char16_t const\*|\<location>|Ahoj světe|  
|S8|const char *|\<location>|Hello World|  
|hod|Kód chyby HRESULT nebo Win32. (Ladicí program nyní dekóduje HRESULTs automaticky, takže tento specifikátor není v těchto případech vyžadován.|S_OK|S_OK|  
|wc|Příznak třídy okna|0x00000040|WC_DEFAULTCHAR|  
|WM|Čísla zpráv systému Windows|0x0010|WM_CLOSE|  
|!|nezpracovaný formát, který ignoruje přizpůsobení zobrazení datových typů|\<customized representation>|4|  
  
### <a name="format-specifiers-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Specifikátory formátu umístění v paměti v ladění spolupráce s C++/CLI  
 Následující tabulka obsahuje symboly formátování používané pro umístění v paměti. Můžete použít specifikátor umístění v paměti s libovolnou hodnotou nebo výrazem, který je vyhodnocen jako umístění.  
  
|Symbol|Formát|Původní hodnota kukátka|Zobrazená hodnota|  
|------------|------------|--------------------------|---------------------|  
|**Vy**|64 znaků ASCII|0x0012ffac|0x0012ffac. 4... 0.... 0W&....... 1T&.0.: W... 1.... ".... 1.JO&.1,2... 1... 0y.... první|  
|**4m**|16 bajtů v šestnáctkové soustavě následovaný 16 znaky ASCII|0x0012ffac|0x0012ffac B3 34 z 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0.... 0W&..|  
|**MB**|16 bajtů v šestnáctkové soustavě následovaný 16 znaky ASCII|0x0012ffac|0x0012ffac B3 34 z 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0.... 0W&..|  
|**MW**|8 slov|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**MD**|4 doubleword|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**MQ**|2 quadword|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**samohlásk**|2 bajty znaků (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 FFFF FFFF 0000 0000 0000 0000|  
  
### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-cclit"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Specifikátor velikosti pro ukazatele jako pole v ladění spolupráce s C++/CLIt  
 Pokud máte ukazatel na objekt, který chcete zobrazit jako pole, můžete použít celé číslo k určení počtu prvků pole:  
  
|Specifikátor|Formát|Výraz|Zobrazená hodnota|  
|---------------|------------|----------------|---------------------|  
|n|Desítkové celé číslo|pBuffer [32]|Zobrazí se `pBuffer` jako pole elementu 32.|
