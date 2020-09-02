---
title: Specifikátory formátu v jazyce C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
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
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6085ba95d3880417e517530069734052741113e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682487"
---
# <a name="format-specifiers-in-c"></a>Specifikátory formátu v jazyce C\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit formát, ve kterém se hodnota zobrazuje v okně **kukátka** , pomocí specifikátorů formátu. Můžete také použít specifikátory formátu v **příkazovém** okně, v **příkazovém** okně a dokonce i ve zdrojových oknech. Pokud v těchto oknech pozastavíte výraz, výsledek se zobrazí v DataTip. Datové tipy budou odrážet specifikátor formátu v zobrazení DataTip.

Chcete-li použít specifikátor formátu, zadejte výraz následovaný čárkou. Za čárku přidejte příslušný specifikátor.

## <a name="using-format-specifiers"></a>Použití specifikátorů formátu

Pokud máte následující kód:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Přidejte `my_var1` proměnnou do okno kukátko (při ladění, **ladění/Windows/sledování/kukátko 1**) a nastavte zobrazení na hexadecimální (v okně **kukátko** klikněte pravým tlačítkem myši na proměnnou a vyberte **hexadecimální zobrazení**). Nyní okno **kukátka** ukazuje, že obsahuje hodnotu 0x0065. Chcete-li zobrazit tuto hodnotu vyjádřenou jako desítkové celé číslo namísto hexadecimálního celého čísla, do sloupce název za název proměnné přidejte specifikátor desítkového formátu: **, d**. Sloupec Value nyní zobrazuje desítkovou hodnotu 101

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

## <a name="format-specifiers"></a>Specifikátory formátu

V následující tabulce jsou uvedeny specifikátory formátu C# rozpoznávané ladicím programem.

|Specifikátor|Formát|Původní hodnota kukátka|Uvádí|
|---------------|------------|--------------------------|--------------|
|proud|Vynutí vyhodnocení výrazu. To může být užitečné, pokud je vypnuto implicitní vyhodnocení vlastností a volání implicitních funkcí. Podívejte [se na vedlejší účinky a výrazy](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|Zpráva "implicitní vyhodnocení funkce je vypnuto uživatelem"|\<value>|
|d|desítkové celé číslo|0x0065|101|
|dynamic|Zobrazí zadaný objekt pomocí dynamického zobrazení.|Zobrazí všechny členy objektu, včetně dynamického zobrazení.|Zobrazí pouze dynamické zobrazení.|
|h|šestnáctkové celé číslo|61541|0x0000F065|
|nq|řetězec bez uvozovek|"Můj řetězec"|Můj řetězec|
|hidden|Zobrazí všechny veřejné a neveřejné členy.|Zobrazí veřejné členy.|Zobrazí všechny členy.|
|získání|Zobrazí položku tak, jak se zobrazuje v uzlu nezpracované položky. Platí pouze pro proxy objekty.|Slovník\<T>|Nezpracované zobrazení slovníku\<T>|
|výsledky|Používá se s proměnnou typu, který implementuje rozhraní IEnumerable nebo IEnumerable \<T> , obvykle výsledek výrazu dotazu. Zobrazí pouze členy, které obsahují výsledek dotazu.|Zobrazí všechny členy.|Zobrazí členy, které splňují podmínky dotazu.|

## <a name="see-also"></a>Viz také

- [Okna Kukátko a Rychlé kukátko](../debugger/watch-and-quickwatch-windows.md)
- [Okna proměnných](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
