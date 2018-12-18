---
title: Formát specifikátorů v ladicím programu (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 73cd5655a5cb843c29fb628a2ec233860410dc7c
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305738"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Specifikátory formátu pro C++ v ladicím programu sady Visual Studio
Můžete změnit formát, ve kterém se zobrazí hodnota v **Watch** okna pomocí specifikátorů formátu.  
  
 Můžete také použít specifikátory formátu v **okamžité** okně **příkaz** okno v [zarážky s trasováním](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)a dokonce i ve zdrojových oknech. Pokud pozastavíte výraz v těchto oknech, výsledek se zobrazí v [datového tipu](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Zobrazení datového tipu odráží specifikátor formátu.  
  
> [!NOTE]
>  Při změně nativní ladicí program sady Visual Studio do nového modulu pro ladění, přidání některých nových specifikátorů formátu a některých jejich starých verzí byly odebrány. Starší ladicí program je stále používán, když provedete spolupráce (smíšená nativní a spravovaná) ladění s C + +/ CLI. 
  
## <a name="set-format-specifiers"></a>Specifikátory formátu sady  
Použijeme následující příklad kódu:  
  
```C++  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Přidat `my_var1` proměnnou **Watch** okno při ladění, **ladění** > **Windows** > **sledovat**  >  **Sledovat 1**. V dalším kroku klikněte pravým tlačítkem na proměnnou a vyberte **hexadecimální zobrazení**. Nyní **Watch** okno zobrazuje hodnota 0x0065. Pokud chcete zobrazit tuto hodnotu vyjádřenou jako znak namísto celého čísla, nejprve klikněte pravým tlačítkem myši a zrušte zaškrtnutí možnosti **hexadecimální zobrazení**. Pak přidejte specifikátor formátu znaku **c** v **název** sloupec za název proměnné. **Hodnotu** sloupec teď zobrazuje **101 "e"**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specifikátory formátu  
 Následující tabulky popisují specifikátory formátu, které můžete použít v sadě Visual Studio. Specifikátory tučným písmem jsou podporovány pouze pro nové ladicí program a ne pro definiční ladění v jazyce C + +/ CLI.  
  
|Specifikátor|Formát|Původní hodnota Watch|Zobrazená hodnota|  
|---------------|------------|--------------------------|---------------------|  
|d|Desítkové celé číslo|0x00000066|102|  
|O|osmičkové celé číslo bez znaménka|0x00000066|000000000146|  
|x<br /><br /> **h**|Šestnáctkové celé číslo|102|0xCCCCCCCC|  
|X<br /><br /> **H**|Šestnáctkové celé číslo|102|0xCCCCCCCC|  
|c|jeden znak|0x0065, c|101 "e"|  
|s|const char * string (v uvozovkách)|\<umístění > "hello world"|"hello world"|  
|**sb**|const char * řetězec (bez uvozovek)|\<umístění > "hello world"|Ahoj světe|  
|s8|Řetězec UTF-8|\<umístění > "Toto je â˜• Šálek kávy UTF-8"|"Toto je ☕ Šálek kávy UTF-8"|
|**s8b**|Řetězec UTF-8 (bez uvozovek)|\<umístění > "hello world"|Ahoj světe|  
|su|Řetězec znaků Unicode (UTF-16 kódování) (v uvozovkách)|\<umístění > L "hello world"|L "hello world"<br /><br /> u "hello world"|  
|Sub|Řetězec znaků Unicode (UTF-16 kódování) (bez uvozovek)|\<umístění > L "hello world"|Ahoj světe|  
|bstr|Řetězec BSTR binární (v uvozovkách)|\<umístění > L "hello world"|L "hello world"|  
|env|Blok prostředí (double null ukončenou string)|\<umístění > L "=:: =::\\\\"|L "=:: =::\\\\\\0 = C: = C:\\\\windows\\\\system32\\0ALLUSERSPROFILE =...|
|**s32**|Řetězec UTF-32 (v uvozovkách)|\<umístění > U "hello world"|u "hello world"|  
|**s32b**|Řetězec UTF-32 (bez uvozovek)|\<umístění > U "hello world"|Ahoj světe|  
|**cs**|enum|Saturday(6)|Sobota|  
|**hv**|Typ ukazatele – označuje, že hodnota ukazatele kontrolován je výsledek přidělení haldy pole, například `new int[3]`.|\<umístění > {\<prvního člena >}|\<umístění > {\<prvního člena >, \<second – člen >,...}|  
|**na**|Potlačí adresa paměti ukazatele na objekt.|\<umístění >, {člen = hodnota...}|{člen = hodnota...}|  
|**ND.**|Zobrazí pouze základní informace o třídě, ignoruje odvozené třídy|`(Shape*) square` zahrnuje základní třída a odvozené informace o třídě|Zobrazí pouze základní informace o třídě|  
|hr|Kód chyby HRESULT nebo Win32. Tento specifikátor je už je nepotřebujete pro HRESULT jako ladicí program dekóduje je automaticky.|S_OK|S_OK|  
|RC|Příznak třídy okna|0x0010|WC_DEFAULTCHAR|  
|wm|Čísla zpráv Windows|16|WM_CLOSE|  
|!|Formát RAW ignorující přizpůsobení zobrazení typu všech dat|\<přizpůsobit reprezentace >|4|  
  
> [!NOTE]
>  Když **hv** je k dispozici specifikátor formátu, ladicí program se pokusí zjistit délku vyrovnávací paměti a zobrazit tento počet prvků. Protože není vždy možné pro ladicí program najít přesnou vyrovnávací paměti velikost pole, měli byste používat specifikátor velikosti `(pBuffer,[bufferSize])` kdykoli je to možné. **Hv** specifikátor formátu je užitečné, když velikost vyrovnávací paměti není snadno k dispozici  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Velikost specifikátoru pro ukazatele jako pole  
 Pokud máte ukazatel na objekt, který chcete zobrazit v poli, můžete použít k zadání počtu elementů pole celé číslo nebo výraz. 
  
|Specifikátor|Formát|Původní hodnota Watch|Zobrazená hodnota|  
|---------------|------------|---------------------------|---------------------|  
|n|Desetinné nebo **šestnáctkové** celé číslo|pBuffer [32]<br /><br /> pBuffer,**[0x20]**|Zobrazí `pBuffer` jako 32 prvek pole.|  
|**[exp]**|Platný výraz jazyka C++, který je vyhodnocen jako celé číslo.|pBuffer [bufferSize]|Zobrazí pBuffer jako pole `bufferSize` elementy.|  
|**expand(n)**|Platný výraz jazyka C++, který je vyhodnocen jako celé číslo|pBuffer, expand(2)|Zobrazí třetího prvku pole  `pBuffer`|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Specifikátory formátu pro interop ladění s C + +/ CLI  
 Specifikátory **tučné** jsou podporovány pouze pro nativní ladění C + +/ CLI kódu.  
  
|Specifikátor|Formát|Původní hodnota Watch|Zobrazená hodnota|  
|---------------|------------|--------------------------|---------------------|  
|**d**<br /><br />**i**|desítkové celé číslo se znaménkem|0xF000F065|-268373915|  
|**u**|desítkové celé číslo bez znaménka|0x0065|101|  
|O|osmičkové celé číslo bez znaménka|0xF065|0170145|  
|x<br /><br />X|Šestnáctkové celé číslo|61541|0x0000f065|  
|**l**<br /><br />**h**|dlouhé nebo krátké předpony pro: d, i, u, e, x, X|00406042|0x0c22|  
|**f**|podepsané s plovoucí desetinnou čárkou|(3. / 2.), f|1.500000|  
|**e**|matematický zápis se znaménkem|(3.0/2.0)|1.500000e + 000|  
|**g**|plovoucí desetinná čárka nebo matematický zápis se znaménkem<br/> podle toho, co je kratší|(3.0/2.0)|1.5|  
|c|jeden znak|\<umístění >|101 "e"|  
|s|const char * (v uvozovkách)|\<umístění >|"hello world"|  
|su|konstantní wchar_t *<br /><br /> Const char16_t\* (v uvozovkách)|\<umístění >|L "hello world"|  
|Sub|konstantní wchar_t *<br /><br /> Const char16_t\*|\<umístění >|Ahoj světe|  
|s8|const char * (v uvozovkách)|\<umístění >|"hello world"|  
|hr|Kód chyby HRESULT nebo Win32.<br/>Tento specifikátor je už je nepotřebujete pro HRESULT jako ladicí program dekóduje je automaticky.|S_OK|S_OK|  
|RC|Příznak třídy okna|0x00000040,|WC_DEFAULTCHAR|  
|wm|Čísla zpráv Windows|0x0010|WM_CLOSE|  
|!|Formát RAW ignorující veškerá přizpůsobení zobrazení typu dat|\<přizpůsobit reprezentace >|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Formát specifikátorů pro paměťových míst v interoperabilním ladění s C + +/ CLI  
 Následující tabulka popisuje symboly formátování použité pro místo v paměti. Specifikátor vyhledávání v paměti můžete použít s libovolnou hodnotou nebo výraz, který je vyhodnocován na místo.  
  
|Symbol|Formát|Původní hodnota Watch|Zobrazená hodnota|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 znaků ASCII|0x0012ffac|0x0012ffac. 4... 0... ". 0W &... 1T &.0.:W... 1... ". 1. JO &.1.2.. ".. 1... 0y... 1|  
|**m**|16 bajtů v šestnáctkovém formátu, následovaný 16 znaky ASCII|0x0012ffac|0X0012FFAC B3 34 FF CB 00 84 30 94 80 22 8A 30 57 26 00 00. 4... 0... ". 0W &...|  
|**MB**|16 bajtů v šestnáctkovém formátu, následovaný 16 znaky ASCII|0x0012ffac|0X0012FFAC B3 34 FF CB 00 84 30 94 80 22 8A 30 57 26 00 00. 4... 0... ". 0W &...|  
|**mw**|8 slova|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 x doubleword|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 x quadword|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|2bajtové znaky (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Velikost specifikátoru pro ukazatele jako pole v interoperabilním ladění s C + +/ CLI  
 Pokud máte ukazatel na objekt, který chcete zobrazit v poli, můžete k zadání počtu elementů pole celé číslo.
  
|Specifikátor|Formát|Výraz|Zobrazená hodnota|  
|---------------|------------|----------------|---------------------|  
|n|Desítkové celé číslo|pBuffer [32]|Zobrazí `pBuffer` jako 32 prvek pole.|
