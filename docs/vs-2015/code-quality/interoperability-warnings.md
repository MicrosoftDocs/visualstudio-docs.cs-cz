---
title: Upozornění na interoperabilitu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fd914a65ff23b05130cb0c36162bb96a3d30aa52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656493"
---
# <a name="interoperability-warnings"></a>Upozornění interoperability
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upozornění na interoperabilitu podporují interakci s klienty modelu COM.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1400: vstupní body volání nespravovaného volání by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Veřejná nebo chráněná metoda je označena pomocí atributu System.Runtime.InteropServices.DllImportAttribute. Nespravovanou knihovnu nelze nalézt nebo nelze metodu porovnat s funkcí v knihovně.|
|[CA1401: volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Veřejná nebo chráněná metoda ve veřejném typu má atribut System.Runtime.InteropServices.DllImportAttribute (také implementováno pomocí klíčového slova Declare v Visual Basic). Tyto metody by neměly být vystaveny.|
|[CA1402: Vyhněte se přetížení ve viditelných rozhraních modelu COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Když jsou přetížené metody vystaveny klientům modulu COM, zachová svůj název pouze první přetížení metody. Následná přetížení jsou jednoznačně přejmenována přidáním podtržítka (_) a celého čísla odpovídajícího pořadí deklarace tohoto přetížení.|
|[CA1403: Typy automatického rozložení by neměly být viditelné modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typ hodnoty viditelný v modelu COM je označen pomocí atributu System. Runtime. InteropServices. StructLayoutAttribute nastaveného na hodnotu LayoutKind. auto. Rozložení těchto typů se může změnit mezi verzemi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , což způsobí přerušení klientů modelu COM, kteří očekávají konkrétní rozložení.|
|[CA1404: volejte GetLastError hned po volání nespravovaného volání](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Bylo provedeno volání metody Marshal. GetLastWin32Error nebo ekvivalentní [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] Funkce GetLastError a bezprostředně předchozí volání není k metodě vyvolání platformy.|
|[CA1405: Základní typy viditelného typu modelu COM by měly být viditelné modelu COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Typ viditelný modulem COM je odvozen od typu, který není viditelný modulem COM.|
|[CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Klienti modelu COM Visual Basic 6 nemají přístup k 64 celých čísel.|
|[CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Modul COM nepodporuje statické metody.|
|[CA1408: Nepoužívejte typ AutoDual ClassInterface](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Typy, které používají duální rozhraní, umožňují klientům navázat se na určité rozložení rozhraní. Změny v budoucí verzi rozložení typu nebo jakéhokoli základního typu přeruší klienty modulu COM, kteří jsou navázáni na toto rozhraní. Pokud ve výchozím nastavení není zadán atribut ClassInterfaceAttribute, použije se pouze rozhraní určené pro odesílání.|
|[CA1409: Viditelné typy modelu COM by měly být vytvořitelné](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Odkazový typ, který je označen jako viditelný modulům COM, obsahuje veřejný parametrizovaný konstruktor, ale neobsahuje veřejný výchozí konstruktor (bez parametrů). Typ bez veřejného výchozího konstruktoru není možné vytvořit klienty typu COM.|
|[CA1410: Metody registrace modelu COM by si měly odpovídat](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Typ deklaruje metodu, která je označena pomocí <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributu, ale nedeklaruje metodu, která je označena pomocí <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributu nebo naopak.|
|[CA1411: Metody registrace modelu COM by neměly být viditelné](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Metoda, která je označena atributem System. Runtime. InteropServices. ComRegisterFunctionAttribute nebo atributem System. Runtime. InteropServices. ComUnregisterFunctionAttribute, je externě viditelná.|
|[CA1412: Označte rozhraní ComSource jako IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Typ je označen atributem System.Runtime.InteropServices.ComSourceInterfacesAttribute a alespoň jedno ze zadaných rozhraní není označeno pomocí atributu System.Runtime.InteropServices.InterfaceTypeAttribute nastaveného na hodnotu ComInterfaceType.InterfaceIsIDispatch.|
|[CA1413: Vyhněte se neveřejným polím v typech hodnot viditelných modulem COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Neveřejná pole instancí hodnotových typů viditelných moduly COM jsou viditelná klientům typu COM. Zkontrolujte obsah polí, zda neobsahují informace, které by neměly být vystaveny nebo které budou mít nežádoucí účinky na návrh nebo zabezpečení.|
|[CA1414: označte logické argumenty P/Invoke s MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Datový typ Boolean má v nespravovaném kódu různé reprezentace.|
|[CA1415: deklarujte správně volání nespravovaných kódů](../code-quality/ca1415-declare-p-invokes-correctly.md)|Toto pravidlo vyhledá deklarace metod vyvolání platformy, které cílí [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] na funkce, které mají ukazatel na PŘEkrývající se parametr struktury, a odpovídající spravovaný parametr není ukazatel na <xref:System.Threading.NativeOverlapped?displayProperty=fullName> strukturu.|
