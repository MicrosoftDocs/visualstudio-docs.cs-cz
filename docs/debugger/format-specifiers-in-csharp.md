---
title: Formát specifikátorů v ladicím programu (C#) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/21/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9c69792b5f925141b95d28a5e2c5255e12011668
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305387"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Specifikátory ve formátu C# v ladicím programu sady Visual Studio
Můžete změnit formát, ve kterém se zobrazí hodnota v **Watch** okna pomocí specifikátorů formátu. Můžete také použít specifikátory formátu v **okamžité** okně **příkaz** okno v [zarážky s trasováním](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)a ve zdrojových oknech. Pokud pozastavíte výraz v těchto oknech, výsledek se zobrazí v [datového tipu](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) v zadaném formátu zobrazení.  
  
 Použití specifikátoru formátu, zadejte výraz proměnné, za nímž následuje čárka a odpovídající specifikátor.  
  
## <a name="set-format-specifiers"></a>Specifikátory formátu sady  
Použijeme následující příklad kódu:   
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Přidat `my_var1` proměnnou **Watch** okno při ladění, **ladění** > **Windows** > **sledovat**  >  **Sledovat 1**. V dalším kroku klikněte pravým tlačítkem na proměnnou a vyberte **hexadecimální zobrazení**. Nyní **Watch** okno zobrazuje hodnota 0x0065. Chcete-li zobrazit tuto hodnotu jako desítkové celé číslo, spíše než šestnáctkové celé číslo, přidejte specifikátor formátu desítkové soustavy **, d** v **název** sloupec za název proměnné. **Hodnotu** sloupec teď zobrazuje **101**.   
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Specifikátory formátu  
 V následující tabulce jsou popsány C# formát specifikátoru v ladicím programu sady Visual Studio.  
  
|Specifikátor|Formát|Původní hodnota Watch|Zobrazí|  
|---------------|------------|--------------------------|--------------|  
|ac|Vynucení vyhodnocení výrazu, které mohou být užitečné, když je vypnutý implicitní vyhodnocování vlastností a implicitních volání funkcí.|Zpráva "implicitní vyhodnocení funkce vypnul uživatel"|\<Hodnota >|  
|d|Desítkové celé číslo|0x0065|101|  
|dynamické odkazy|Zobrazí zadaný objekt pomocí dynamického zobrazení|Zobrazí všechny členy objektu, včetně dynamického zobrazení|Zobrazí pouze dynamické zobrazení|  
|h|Šestnáctkové celé číslo|61541|0x0000F065|  
|NQ|řetězec s žádné uvozovky|"String"|Moje řetězec|  
|nse|Určuje chování, není formát. Vyhodnotí výraz s "Žádné vedlejší účinky". Pokud výraz se nedá interpretovat a lze vyřešit pouze zkušební verzi (jako je například volání funkce), zobrazí se chyba místo.|Není k dispozici|Není k dispozici|
|hidden|Zobrazí všechny veřejné a neveřejné členy|Zobrazí veřejné členy|Zobrazí všechny členy|  
|nezpracované|Zobrazí položky, jak se zobrazí v uzlu nezpracovaná položka. Platí pouze pro objekty proxy.|Slovník\<T >|Nezpracované zobrazení, slovníku\<T >|  
|výsledky|Použít s proměnnou typu, který implementuje rozhraní IEnumerable nebo IEnumerable\<T >, obvykle výsledek výrazu dotazu. Zobrazí pouze členy, které obsahují výsledku dotazu.|Zobrazí všechny členy|Zobrazí členy, splňují podmínky dotazu|  
  
## <a name="see-also"></a>Viz také:  
 [Kukátko a Rychlé kukátko](../debugger/watch-and-quickwatch-windows.md)   
 [Okna Automatické hodnoty a místní hodnoty](../debugger/autos-and-locals-windows.md)
