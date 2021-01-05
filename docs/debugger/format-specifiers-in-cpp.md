---
title: Specifikátory formátu v ladicím programu (C++) | Microsoft Docs
description: Použijte specifikátor formátu ke změně formátu, ve kterém se hodnota zobrazuje v okně kukátko, automatické hodnoty a místní hodnoty. Tento článek poskytuje podrobné informace o využití.
ms.custom: SEO-VS-2020
ms.date: 3/11/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 74b6b6b6a8f7a9f5f234a9b46c799e6e0580536f
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761326"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Specifikátory formátu pro C++ v ladicím programu sady Visual Studio
Můžete změnit formát, ve kterém se hodnota zobrazuje v oknech **kukátko**, **Automatické** hodnoty a **místní** hodnoty pomocí specifikátorů formátu.

Můžete také použít specifikátory formátu v **příkazovém** okně, v **příkazovém** okně, v [trasováním](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)a dokonce i ve zdrojových oknech. Pokud v těchto oknech pozastavíte výraz, výsledek se zobrazí v [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Zobrazení DataTip odráží specifikátor formátu.

> [!NOTE]
> Po změně nativního ladicího programu sady Visual Studio na nový ladicí stroj byly přidány některé nové specifikátory formátu a některé staré byly odebrány. Starší ladicí program se pořád používá, když provedete spolupráci (smíšené nativní a spravované) ladění s využitím C++/CLI.

## <a name="set-format-specifiers"></a>Nastavit specifikátory formátu
Použijeme následující příklad kódu:

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Přidat `my_var1` proměnnou do okna **kukátka** během ladění, **ladit**  >    >  **kukátko** kukátko  >  **1**. Potom klikněte pravým tlačítkem na proměnnou a vyberte **hexadecimální zobrazení**. Nyní okno **kukátka** zobrazuje hodnotu 0x0065. Chcete-li zobrazit tuto hodnotu vyjádřenou jako znak, a ne jako celé číslo, napřed klikněte pravým tlačítkem myši a zrušte výběr **hexadecimálního zobrazení**. Poté do sloupce **název** za název proměnné přidejte specifikátor formátu znaků **, c** . Sloupec **Value** nyní zobrazuje **101 "e"**.

![Snímek obrazovky sady Visual Studio okno Kukátko s jedním vybraným řádkem, který zobrazuje my_var1. c s hodnotou 101 ' e ' a typem int.](../debugger/media/watchformatcplus1.png)

::: moniker range=">= vs-2019" 
Můžete zobrazit a vybrat ze seznamu dostupných specifikátorů formátu připojením čárky (,) k hodnotě v okně **kukátko** . 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specifikátory formátu
V následujících tabulkách jsou popsány specifikátory formátu, které lze použít v aplikaci Visual Studio. Specifikátory tučným písmem jsou podporovány pouze pro nový ladicí program, nikoli pro spolupráci s C++/CLI.

::: moniker range=">= vs-2019" 

|Specifikátor|Formát|Původní hodnota kukátka|Zobrazená hodnota|
|---------------|------------|--------------------------|---------------------|
|d|desítkové celé číslo|0x00000066|102|
|o|osmičkové celé číslo bez znaménka|0x00000066|000000000146|
|x<br /><br /> **h**|šestnáctkové celé číslo|102|0xcccccccc|
|X<br /><br /> **Y**|šestnáctkové celé číslo|102|0xCCCCCCCC|
|XB<br /><br /> **nejenom**|šestnáctkové celé číslo (bez úvodní 0x)|102|cccccccc|
|XB<br /><br /> **Nejenom**|šestnáctkové celé číslo (bez úvodní 0x)|102|CCCCCCCC|
|b|binární celé číslo bez znaménka|25|0b00000000000000000000000000011001|
|bb|binární celé číslo bez znaménka (bez úvodní 0b)|25|00000000000000000000000000011001|
|e|vědecká notace|25000000|2.500000 e + 07|
|g|kratší z vědeckých nebo plovoucích bodů|25000000|2,5 e + 07|
|c|jeden znak|0x0065|101 "e"|
|s|const char * String (s uvozovkami)|\<location> Hello World|Hello World|
|**SB**|const char * String (žádné uvozovky)|\<location> Hello World|Ahoj světe|
|S8|Řetězec UTF-8|\<location> "Jedná se o kávové konvičku UTF-8, ̃ •"|"Toto je ☕ v kávě v kódování UTF-8"|
|**s8b**|Řetězec UTF-8 (žádné uvozovky)|\<location> Hello World|Ahoj světe|
|Pá|Řetězec kódování Unicode (UTF-16) (s uvozovkami)|\<location> L "Hello World"|L "Hello World"<br /><br /> u "Hello World"|
|jednotk|Řetězec kódování Unicode (UTF-16) (žádné uvozovky)|\<location> L "Hello World"|Ahoj světe|
|bstr|Binární řetězec BSTR (s uvozovkami)|\<location> L "Hello World"|L "Hello World"|
|ENV|Blok prostředí (řetězec zakončený znakem null)|\<location>L "=:: =:: \\ \\ "|L "=:: =:: \\ \\ \\ 0 = c: = c: \\ \\ Windows \\ \\ system32 \\ 0ALLUSERSPROFILE =...|
|**s32**|Řetězec UTF-32 (s uvozovkami)|\<location> U "Hello World"|U "Hello World"|
|**s32b**|Řetězec UTF-32 (žádné uvozovky)|\<location> U "Hello World"|Ahoj světe|
|**en**|enum|Sobota (6)|Sobota|
|**hv**|Typ ukazatele – určuje, že hodnota kontrolovaného ukazatele je výsledkem přidělení haldy pole, například `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**ná**|Potlačí adresu paměti ukazatele na objekt.|\<location>, {member = Value...}|{member = Value...}|
|**c**|Zobrazí pouze informace základní třídy, ignorování odvozených tříd.|`(Shape*) square` zahrnuje základní třídu a informace o odvozených třídách.|Zobrazí jenom informace o základní třídě.|
|hod|Kód chyby HRESULT nebo Win32. Tento specifikátor již není potřeba pro HRESULTs, protože ladicí program je dekóduje automaticky.|S_OK|S_OK|
|wc|Příznak třídy okna|0x0010|WC_DEFAULTCHAR|
|WM|Čísla zpráv systému Windows|16|WM_CLOSE|
|Nr|Potlačit položku nezpracovaného zobrazení|
|nvo|Zobrazit položku nezpracovaného zobrazení pro číselné hodnoty|
|!|nezpracovaný formát, který ignoruje přizpůsobení zobrazení datových typů|\<customized representation>|4|

::: moniker-end

::: moniker range="vs-2017" 

|Specifikátor|Formát|Původní hodnota kukátka|Zobrazená hodnota|
|---------------|------------|--------------------------|---------------------|
|d|desítkové celé číslo|0x00000066|102|
|o|osmičkové celé číslo bez znaménka|0x00000066|000000000146|
|x<br /><br /> **h**|šestnáctkové celé číslo|102|0xcccccccc|
|X<br /><br /> **Y**|šestnáctkové celé číslo|102|0xCCCCCCCC|
|c|jeden znak|0x0065, c|101 "e"|
|s|const char * String (s uvozovkami)|\<location> Hello World|Hello World|
|**SB**|const char * String (žádné uvozovky)|\<location> Hello World|Ahoj světe|
|S8|Řetězec UTF-8|\<location> "Jedná se o kávové konvičku UTF-8, ̃ •"|"Toto je ☕ v kávě v kódování UTF-8"|
|**s8b**|Řetězec UTF-8 (žádné uvozovky)|\<location> Hello World|Ahoj světe|
|Pá|Řetězec kódování Unicode (UTF-16) (s uvozovkami)|\<location> L "Hello World"|L "Hello World"<br /><br /> u "Hello World"|
|jednotk|Řetězec kódování Unicode (UTF-16) (žádné uvozovky)|\<location> L "Hello World"|Ahoj světe|
|bstr|Binární řetězec BSTR (s uvozovkami)|\<location> L "Hello World"|L "Hello World"|
|ENV|Blok prostředí (řetězec zakončený znakem null)|\<location>L "=:: =:: \\ \\ "|L "=:: =:: \\ \\ \\ 0 = c: = c: \\ \\ Windows \\ \\ system32 \\ 0ALLUSERSPROFILE =...|
|**s32**|Řetězec UTF-32 (s uvozovkami)|\<location> U "Hello World"|U "Hello World"|
|**s32b**|Řetězec UTF-32 (žádné uvozovky)|\<location> U "Hello World"|Ahoj světe|
|**en**|enum|Sobota (6)|Sobota|
|**hv**|Typ ukazatele – určuje, že hodnota kontrolovaného ukazatele je výsledkem přidělení haldy pole, například `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**ná**|Potlačí adresu paměti ukazatele na objekt.|\<location>, {member = Value...}|{member = Value...}|
|**c**|Zobrazí pouze informace základní třídy, ignorování odvozených tříd.|`(Shape*) square` zahrnuje základní třídu a informace o odvozených třídách.|Zobrazí jenom informace o základní třídě.|
|hod|Kód chyby HRESULT nebo Win32. Tento specifikátor již není potřeba pro HRESULTs, protože ladicí program je dekóduje automaticky.|S_OK|S_OK|
|wc|Příznak třídy okna|0x0010|WC_DEFAULTCHAR|
|WM|Čísla zpráv systému Windows|16|WM_CLOSE|
|!|nezpracovaný formát, který ignoruje přizpůsobení zobrazení datových typů|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> Když je přítomen specifikátor formátu **HV** , ladicí program se pokusí určit délku vyrovnávací paměti a zobrazit tento počet prvků. Protože není vždy možné, aby ladicí program mohl najít přesnou velikost vyrovnávací paměti pole, měli byste použít specifikátor velikosti, kdykoli je `(pBuffer,[bufferSize])` to možné. Specifikátor formátu **HV** je užitečný v případě, že velikost vyrovnávací paměti není snadno dostupná.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Specifikátory velikosti pro ukazatele jako pole
Pokud máte ukazatel na objekt, který chcete zobrazit jako pole, můžete použít celé číslo nebo výraz k určení počtu prvků pole.

|Specifikátor|Formát|Původní hodnota kukátka|Zobrazená hodnota|
|---------------|------------|---------------------------|---------------------|
|n|Desítkové nebo **šestnáctkové** celé číslo|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|Zobrazí se `pBuffer` jako pole elementu 32.|
|**oček**|Platný výraz C++, který je vyhodnocen jako celé číslo.|pBuffer, [bufferSize]|Zobrazí pBuffer jako pole `bufferSize` prvků.|
|**Rozbalit (n)**|Platný výraz C++, který se vyhodnotí jako celé číslo|pBuffer, expand (2)|Zobrazí třetí prvek  `pBuffer`|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Specifikátory formátu pro spolupráci při ladění pomocí C++/CLI
Specifikátory **tučným písmem** jsou podporovány pouze pro ladění nativních a C++/CLI kódu.

|Specifikátor|Formát|Původní hodnota kukátka|Zobrazená hodnota|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|desítkové celé číslo se znaménkem|0xF000F065|-268373915|
|**h**|desítkové celé číslo bez znaménka|0x0065|101|
|o|osmičkové celé číslo bez znaménka|0xF065|0170145|
|x<br /><br />X|Šestnáctkové celé číslo|61541|0x0000f065|
|**l**<br /><br />**h**|dlouhá nebo krátká předpona pro: d, i, u, o, x, X|00406042|0x0c22|
|**FJ**|přihlášený plovoucí bod|(3./2.), f|1,500000|
|**cerebrální**|podepsaný vědecký zápis|(3.0/2.0)|1.500000 e + 000|
|**věcn**|přihlášený plovoucí bod nebo podepsaný vědecký zápis<br/> podle toho, co je kratší|(3.0/2.0)|1.5|
|c|jeden znak|\<location>|101 "e"|
|s|const char * (s uvozovkami)|\<location>|Hello World|
|Pá|const wchar_t *<br /><br /> const char16_t \* (s uvozovkami)|\<location>|L "Hello World"|
|jednotk|const wchar_t *<br /><br /> char16_t const\*|\<location>|Ahoj světe|
|S8|const char * (s uvozovkami)|\<location>|Hello World|
|hod|Kód chyby HRESULT nebo Win32.<br/>Tento specifikátor již není potřeba pro HRESULTs, protože ladicí program je dekóduje automaticky.|S_OK|S_OK|
|wc|Příznak třídy okna|0x00000040|WC_DEFAULTCHAR|
|WM|Čísla zpráv systému Windows|0x0010|WM_CLOSE|
|!|nezpracovaný formát, který ignoruje libovolné přizpůsobení zobrazení datového typu|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Specifikátory formátu pro umístění v paměti v ladění spolupráce s C++/CLI
Následující tabulka popisuje symboly formátování používané pro umístění v paměti. Můžete použít specifikátor umístění v paměti s libovolnou hodnotou nebo výrazem, který je vyhodnocen jako umístění.

|Symbol|Formát|Původní hodnota kukátka|Zobrazená hodnota|
|------------|------------|--------------------------|---------------------|
|**Vy**|64 znaků ASCII|0x0012ffac|0x0012ffac. 4... 0.... 0W&....... 1T&.0.: W... 1.... ".... 1.JO&.1,2... 1... 0y.... první|
|**m**|16 bajtů v šestnáctkové soustavě následovaný 16 znaky ASCII|0x0012ffac|0x0012ffac B3 34 z 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0.... 0W&..|
|**MB**|16 bajtů v šestnáctkové soustavě následovaný 16 znaky ASCII|0x0012ffac|0x0012ffac B3 34 z 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0.... 0W&..|
|**MW**|8 slov|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**MD**|4 doubleword|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**MQ**|2 quadword|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**samohlásk**|2 bajty znaků (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 FFFF FFFF 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Specifikátor velikosti pro ukazatele jako pole v ladění spolupráce s C++/CLI
Pokud máte ukazatel na objekt, který chcete zobrazit jako pole, můžete použít celé číslo k určení počtu prvků pole.

|Specifikátor|Formát|Výraz|Zobrazená hodnota|
|---------------|------------|----------------|---------------------|
|n|Desítkové celé číslo|pBuffer [32]|Zobrazí se `pBuffer` jako pole 32-element.|