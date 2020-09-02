---
title: Upozornění interoperability
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74bffffa2b4f95aeab20438199bb19693a1a3b94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235118"
---
# <a name="interoperability-warnings"></a>Upozornění interoperability

Upozornění na interoperabilitu podporují interakci s klienty modelu COM.

## <a name="in-this-section"></a>V tomto oddílu

| Pravidlo | Popis |
| - | - |
| [CA1400: vstupní body volání nespravovaného volání by měly existovat](../code-quality/ca1400.md) | Veřejná nebo chráněná metoda je označena pomocí atributu System.Runtime.InteropServices.DllImportAttribute. Nespravovanou knihovnu nelze nalézt nebo nelze metodu porovnat s funkcí v knihovně. |
| [CA1401: volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401.md) | Veřejná nebo chráněná metoda ve veřejném typu má atribut System.Runtime.InteropServices.DllImportAttribute (také implementováno pomocí klíčového slova Declare v Visual Basic). Tyto metody by neměly být vystaveny. |
| [CA1402: Vyhněte se přetížení ve viditelných rozhraních modelu COM](../code-quality/ca1402.md) | Když jsou přetížené metody vystaveny klientům modulu COM, zachová svůj název pouze první přetížení metody. Následná přetížení jsou jednoznačně přejmenována přidáním podtržítka (_) a celého čísla odpovídajícího pořadí deklarace tohoto přetížení. |
| [CA1403: Typy automatického rozložení by neměly být viditelné modelu COM](../code-quality/ca1403.md) | Typ hodnoty viditelný v modelu COM je označen pomocí atributu System. Runtime. InteropServices. StructLayoutAttribute nastaveného na hodnotu LayoutKind. auto. Rozložení těchto typů se může změnit mezi verzemi .NET, čímž dojde k přerušení klientů modelu COM, které očekávají konkrétní rozložení. |
| [CA1404: volejte GetLastError hned po volání nespravovaného volání](../code-quality/ca1404.md) | Bylo provedeno volání metody Marshal. GetLastWin32Error nebo ekvivalentní [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] Funkce GetLastError a bezprostředně předchozí volání není k metodě vyvolání platformy. |
| [CA1405: Základní typy viditelného typu modelu COM by měly být viditelné modelu COM](../code-quality/ca1405.md) | Typ viditelný modulem COM je odvozen od typu, který není viditelný modulem COM. |
| [CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6](../code-quality/ca1406.md) | Klienti modelu COM Visual Basic 6 nemají přístup k 64 celých čísel. |
| [CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407.md) | Modul COM nepodporuje statické metody. |
| [CA1408: Nepoužívejte typ AutoDual ClassInterface](../code-quality/ca1408.md) | Typy, které používají duální rozhraní, umožňují klientům navázat se na určité rozložení rozhraní. Změny v budoucí verzi rozložení typu nebo jakéhokoli základního typu přeruší klienty modulu COM, kteří jsou navázáni na toto rozhraní. Pokud ve výchozím nastavení není zadán atribut ClassInterfaceAttribute, použije se pouze rozhraní určené pro odesílání. |
| [CA1409: Viditelné typy modelu COM by měly být vytvořitelné](../code-quality/ca1409.md) | Odkazový typ, který je označen jako viditelný modulům COM, obsahuje veřejný parametrizovaný konstruktor, ale neobsahuje veřejný výchozí konstruktor (bez parametrů). Typ bez veřejného výchozího konstruktoru není možné vytvořit klienty typu COM. |
| [CA1410: Metody registrace modelu COM by si měly odpovídat](../code-quality/ca1410.md) | Typ deklaruje metodu, která je označena pomocí <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributu, ale nedeklaruje metodu, která je označena pomocí <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributu nebo naopak. |
| [CA1411: Metody registrace modelu COM by neměly být viditelné](../code-quality/ca1411.md) | Metoda, která je označena atributem System. Runtime. InteropServices. ComRegisterFunctionAttribute nebo atributem System. Runtime. InteropServices. ComUnregisterFunctionAttribute, je externě viditelná. |
| [CA1412: Označte rozhraní ComSource jako IDispatch](../code-quality/ca1412.md) | Typ je označen atributem System.Runtime.InteropServices.ComSourceInterfacesAttribute a alespoň jedno ze zadaných rozhraní není označeno pomocí atributu System.Runtime.InteropServices.InterfaceTypeAttribute nastaveného na hodnotu ComInterfaceType.InterfaceIsIDispatch. |
| [CA1413: Vyhněte se neveřejným polím v typech hodnot viditelných modulem COM](../code-quality/ca1413.md) | Neveřejná pole instancí hodnotových typů viditelných moduly COM jsou viditelná klientům typu COM. Zkontrolujte obsah polí, zda neobsahují informace, které by neměly být vystaveny nebo které budou mít nežádoucí účinky na návrh nebo zabezpečení. |
| [CA1414: označte logické argumenty P/Invoke s MarshalAs](../code-quality/ca1414.md) | Datový typ Boolean má v nespravovaném kódu různé reprezentace. |
| [CA1415: deklarujte správně volání nespravovaných kódů](../code-quality/ca1415.md) | Toto pravidlo vyhledá deklarace metod vyvolání platformy, které cílí [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] na funkce, které mají ukazatel na PŘEkrývající se parametr struktury, a odpovídající spravovaný parametr není ukazatel na <xref:System.Threading.NativeOverlapped?displayProperty=fullName> strukturu. |
| [CA1417: Nepoužívejte pro `OutAttribute` řetězcové parametry pro volání nespravovaného volání.](../code-quality/ca1417.md) | Řetězcové parametry předávané hodnotou s `OutAttribute` může destabilizovat modul runtime, pokud je řetězec interně řetězec. |