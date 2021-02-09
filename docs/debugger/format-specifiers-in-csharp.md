---
title: Specifikátory formátu v ladicím programu (C#) | Microsoft Docs
description: Použijte specifikátor formátu ke změně formátu, ve kterém je hodnota zobrazená v okno Kukátko. Tento článek poskytuje podrobné informace o využití.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: abc824cf5d0413f01ad5f3f4423b974aeca40b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870581"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Specifikátory formátu v jazyce C# v ladicím programu sady Visual Studio
Můžete změnit formát, ve kterém se hodnota zobrazuje v okně **kukátka** , pomocí specifikátorů formátu. Můžete také použít specifikátory formátu v **příkazovém** okně, v **příkazovém** okně v [trasováním](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)a ve zdrojových oknech. Pokud v těchto oknech pozastavíte výraz, výsledek se zobrazí v  [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) v zadaném formátu.

Chcete-li použít specifikátor formátu, zadejte výraz proměnné následovaný čárkou a odpovídajícím specifikátorem.

## <a name="set-format-specifiers"></a>Nastavit specifikátory formátu
Použijeme následující příklad kódu:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Přidat `my_var1` proměnnou do okna **kukátka** během ladění, **ladit**  >    >  **kukátko** kukátko  >  **1**. Potom klikněte pravým tlačítkem na proměnnou a vyberte **hexadecimální zobrazení**. Nyní okno **kukátka** zobrazuje hodnotu 0x0065. Chcete-li zobrazit tuto hodnotu jako desítkové celé číslo, nikoli hexadecimální celé číslo, přidejte specifikátor desítkového formátu **d** ve sloupci **název** za název proměnné. Sloupec **Value** nyní zobrazuje **101**.

![Snímek obrazovky sady Visual Studio okno Kukátko s jedním řádkem, který zobrazuje my_var1, d s hodnotou 101 a typem int.](../debugger/media/watchformatcsharp.png)

::: moniker range=">= vs-2019" 

Můžete zobrazit a vybrat ze seznamu dostupných specifikátorů formátu připojením čárky (,) k hodnotě v okně **kukátko** . 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Specifikátory formátu
Následující tabulka popisuje specifikátory formátu C# pro ladicí program sady Visual Studio.

|Specifikátor|Formát|Původní hodnota kukátka|Uvádí|
|---------------|------------|--------------------------|--------------|
|proud|Vynutí vyhodnocení výrazu, který může být užitečný, pokud je vypnuto implicitní vyhodnocení vlastností a volání implicitních funkcí.|Zpráva "implicitní vyhodnocení funkce je vypnuto uživatelem"|\<value>|
|d|desítkové celé číslo|0x0065|101|
|dynamic|Zobrazí zadaný objekt pomocí dynamického zobrazení.|Zobrazí všechny členy objektu, včetně dynamického zobrazení.|Zobrazí pouze dynamické zobrazení.|
|h|šestnáctkové celé číslo|61541|0x0000F065|
|nq|řetězec bez uvozovek|"Můj řetězec"|Můj řetězec|
|nse|Určuje chování, nikoli formát. Vyhodnotí výraz pomocí "žádné vedlejší účinky". Pokud výraz nelze interpretovat a lze jej vyřešit pouze vyhodnocením (například volání funkce), zobrazí se místo toho chyba.|N/A|N/A|
|hidden|Zobrazí všechny veřejné a neveřejné členy.|Zobrazí veřejné členy.|Zobrazí všechny členy.|
|získání|Zobrazí položku tak, jak se zobrazuje v uzlu nezpracované položky. Platí pouze pro proxy objekty.|Slovník\<T>|Nezpracované zobrazení slovníku\<T>|
|výsledky|Používá se s proměnnou typu, který implementuje rozhraní IEnumerable nebo IEnumerable \<T> , obvykle výsledek výrazu dotazu. Zobrazí pouze členy, které obsahují výsledek dotazu.|Zobrazí všechny členy.|Zobrazí členy, které splňují podmínky dotazu.|

## <a name="see-also"></a>Viz také
- [Kukátko a QuickWatch okna](../debugger/watch-and-quickwatch-windows.md)
- [Okna Automatické hodnoty a místní hodnoty](../debugger/autos-and-locals-windows.md)
