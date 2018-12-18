---
title: V jazyce C++ specifikátory formátu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
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
manager: ghogen
ms.openlocfilehash: 6634124e7dc0b50236a9fd6ff9c5c5388c3063bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810517"
---
# <a name="format-specifiers-in-c"></a>Specifikátory formátu v jazyce C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit formát, ve kterém se zobrazí hodnota v **Watch** okna pomocí specifikátorů formátu.  
  
 Můžete také použít specifikátory formátu v **okamžité** okně **příkaz** okna a dokonce i ve zdrojových oknech. Pokud pozastavíte výraz v těchto oknech, výsledek se zobrazí v datovém tipu. Zobrazení datového tipu odráží specifikátor formátu.  
  
> [!NOTE]
>  Visual Studio nativní ladicí program změní na novém ladicím modulu. Jako součást této změně přidání některých nových specifikátorů formátu a některých jejich starých verzí byly odebrány. Starší ladicí program je stále používán, když provedete spolupráce (smíšená nativní a spravovaná) ladění s C + +/ CLI. Následující části v tomto tématu uvádí specifikátory formátu pro každý ladicí stroj.  
> 
> - [Specifikátory formátu](#BKMK_Visual_Studio_2012_format_specifiers) popisuje specifikátory formátu v novém ladicím modulu.  
>   -   [Specifikátory formátu pro interop ladění s C + +/ CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) popisuje specifikátory formátu staršího modulu pro ladění.  
  
## <a name="using-format-specifiers"></a>Použití specifikátorů formátu  
 Pokud máte následující kód:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Přidat `my_var1` proměnnou **Watch** okno (při ladění, **ladění / Windows / sledovat / podívejte se na 1**) a nastavte zobrazení do šestnáctkové soustavy (v **Watch** okna, Klikněte pravým tlačítkem na proměnnou a vyberte **hexadecimální zobrazení**). Okno kukátka teď zobrazuje, že obsahuje hodnotu 0x0065. Chcete-li zobrazit tuto hodnotu vyjádřenou jako znak namísto celého čísla, ve sloupci Název za název proměnné, přidejte specifikátor formátu znaku **c**. **Hodnotu** sloupce se teď zobrazí s **101 "e"**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specifikátory formátu  
 Následující tabulky popisují specifikátory formátu lze použít v sadě Visual Studio. Specifikátory tučným písmem nejsou podporovány pro definiční ladění v jazyce C + +/ CLI.  
  
|Specifikátor|Formát|Původní hodnota Watch|Zobrazená hodnota|  
|---------------|------------|--------------------------|---------------------|  
|d|Desítkové celé číslo|0x00000066|102|  
|O|osmičkové celé číslo bez znaménka|0x00000066|000000000146|  
|x<br /><br /> **h**|Šestnáctkové celé číslo|102|0xCCCCCCCC|  
|X<br /><br /> **H**|Šestnáctkové celé číslo|102|0xCCCCCCCC|  
|c|jeden znak|0x0065, c|101 "e"|  
|s|const char * řetězec|\<umístění > "hello world"|"hello world"|  
|**sb**|const char * řetězec|\<umístění > "hello world"|Ahoj světe|  
|s8|const char * řetězec|\<umístění > "hello world"|"hello world"|  
|**s8b**|const char * řetězec|\<umístění > "hello world"|"hello world"|  
|su|konstantní wchar_t * const<br /><br /> char16_t\* řetězec|\<umístění > L "hello world"|L "hello world"<br /><br /> u "hello world"|  
|Sub|konstantní wchar_t * const<br /><br /> char16_t\* řetězec|\<umístění > L "hello world"|Ahoj světe|  
|bstr|Řetězec BSTR|\<umístění > L "hello world"|L "hello world"|  
|**s32**|Řetězec UTF-32|\<umístění > U "hello world"|U "hello world"|  
|**s32b**|Řetězec UTF-32 (bez uvozovek)|\<umístění > U "hello world"|Ahoj světe|  
|**cs**|enum|Saturday(6)|Sobota|  
|**hv**|Typ ukazatele – označuje, že hodnota ukazatele kontrolován je výsledek přidělení haldy pole, například `new int[3]`.|\<umístění > {\<prvního člena >}|\<umístění > {\<prvního člena >, \<second – člen >,...}|  
|**na**|Potlačí adresa paměti ukazatele na objekt.|\<umístění >, {člen = hodnota...}|{člen = hodnota...}|  
|**ND.**|Zobrazí pouze základní informace o třídě, ignoruje odvozené třídy|`(Shape*) square` zahrnuje základní třída a odvozené informace o třídě|Zobrazí pouze základní informace o třídě|  
|hr|Kód chyby HRESULT nebo Win32. (Ladicí program nyní dekóduje hodnoty HRESULT automaticky, takže v těchto případech není tento specifikátor vyžadován.|S_OK|S_OK|  
|RC|Příznak třídy okna|0x0010|WC_DEFAULTCHAR|  
|wm|Čísla zpráv Windows|16|WM_CLOSE|  
|!|Formát RAW ignorující přizpůsobení zobrazení typu všech dat|\<přizpůsobit reprezentace >|4|  
  
> [!NOTE]
>  Když **hv** je k dispozici specifikátor formátu, ladicí program se pokusí zjistit délku vyrovnávací paměti a zobrazit odpovídající počet prvků. Protože není vždy možné pro ladicí program najít přesnou vyrovnávací paměti velikost pole, měli byste používat specifikátor velikosti `(pBuffer,[bufferSize])` kdykoli je to možné. **Hv** specifikátor formátu je určené pro scénáře, kde velikost vyrovnávací paměti není snadno k dispozici  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Velikost specifikátoru pro ukazatele jako pole  
 Pokud máte ukazatel na objekt, který chcete zobrazit v poli, můžete použít k zadání počtu elementů pole celé číslo nebo výraz:  
  
|Specifikátor|Formát|Původní hodnotaN Watch|Zobrazená hodnota|  
|---------------|------------|---------------------------|---------------------|  
|n|Desetinné nebo **šestnáctkové** celé číslo|pBuffer [32]<br /><br /> pBuffer,**[0x20]**|Zobrazí `pBuffer` jako 32 prvek pole.|  
|**[exp]**|Platný výraz jazyka C++, který je vyhodnocen jako celé číslo.|pBuffer [bufferSize]|Zobrazí pBuffer jako pole `bufferSize` elementy.|  
|**expand(n)**|Platný výraz jazyka C++, který je vyhodnocen jako celé číslo|pBuffer, expand(2)|Zobrazí třetího prvku pole  `pBuffer`|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Specifikátory formátu pro interop ladění s C + +/ CLI  
 Specifikátory **tučné** jsou podporovány pouze pro nativní ladění C + +/ CLI kódu.  
  
|Specifikátor|Formát|Původní hodnota Watch|Zobrazená hodnota|  
|---------------|------------|--------------------------|---------------------|  
|**d, můžu**|desítkové celé číslo se znaménkem|0xF000F065|-268373915|  
|**u**|desítkové celé číslo bez znaménka|0x0065|101|  
|O|osmičkové celé číslo bez znaménka|0xF065|0170145|  
|x,X|Šestnáctkové celé číslo|61541|0x0000f065|  
|**l,h**|dlouhé nebo krátké předpony pro: d, i, u, e, x, X|00406042|0x0c22|  
|**f**|podepsané s plovoucí desetinnou čárkou|(3. / 2.), f|1.500000|  
|**e**|matematický zápis se znaménkem|(3.0/2.0)|1.500000e + 000|  
|**g**|přihlášen s plovoucí desetinnou čárkou nebo matematický zápis se znaménkem, podle toho, co je kratší|(3.0/2.0)|1.5|  
|c|jeden znak|\<umístění >|101 "e"|  
|s|const char *|\<umístění >|"hello world"|  
|su|konstantní wchar_t *<br /><br /> Const char16_t\*|\<umístění >|L "hello world"|  
|Sub|konstantní wchar_t *<br /><br /> Const char16_t\*|\<umístění >|Ahoj světe|  
|s8|const char *|\<umístění >|"hello world"|  
|hr|Kód chyby HRESULT nebo Win32. (Ladicí program nyní dekóduje hodnoty HRESULT automaticky, takže v těchto případech není tento specifikátor vyžadován.|S_OK|S_OK|  
|RC|Příznak třídy okna.|0x00000040,|WC_DEFAULTCHAR|  
|wm|Čísla zpráv Windows|0x0010|WM_CLOSE|  
|!|Formát RAW ignorující přizpůsobení zobrazení typu všech dat|\<přizpůsobit reprezentace >|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Formát specifikátorů paměťových míst v interoperabilním ladění s C + +/ CLI  
 Následující tabulka obsahuje symboly formátování použité pro místo v paměti. Specifikátor vyhledávání v paměti můžete použít s libovolnou hodnotou nebo výraz, který je vyhodnocován na místo.  
  
|Symbol|Formát|Původní hodnota Watch|Zobrazená hodnota|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 znaků ASCII|0x0012ffac|0x0012ffac. 4... 0... ". 0W &... 1T &.0.:W... 1... ". 1. JO &.1.2.. ".. 1... 0y... 1|  
|**m**|16 bajtů v šestnáctkovém formátu, následovaný 16 znaky ASCII|0x0012ffac|0X0012FFAC B3 34 FF CB 00 84 30 94 80 22 8A 30 57 26 00 00. 4... 0... ". 0W &...|  
|**MB**|16 bajtů v šestnáctkovém formátu, následovaný 16 znaky ASCII|0x0012ffac|0X0012FFAC B3 34 FF CB 00 84 30 94 80 22 8A 30 57 26 00 00. 4... 0... ". 0W &...|  
|**mw**|8 slova|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 x doubleword|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 x quadword|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|2bajtové znaky (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Velikost specifikátoru pro ukazatele jako pole v interoperabilním ladění s C + +/ CLIt  
 Pokud máte ukazatel na objekt, který chcete zobrazit v poli, můžete k zadání počtu elementů pole celé:  
  
|Specifikátor|Formát|Výraz|Zobrazená hodnota|  
|---------------|------------|----------------|---------------------|  
|n|Desítkové celé číslo|pBuffer [32]|Zobrazí `pBuffer` jako 32 prvek pole.|





