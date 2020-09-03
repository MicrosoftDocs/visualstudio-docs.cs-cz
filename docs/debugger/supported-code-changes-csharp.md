---
title: Podporované změny kódu (C# a Visual Basic) | Microsoft Docs
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44881035da14483c3ddf1f4c48cb3957a1ce8b50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729093"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Podporované změny kódu (C# a Visual Basic)
Upravit a pokračovat zpracovává většinu typů změn kódu v rámci těla metody. Většina změn mimo tělo metody a několik změn v rámci těla metod nelze použít během ladění. Chcete-li použít tyto nepodporované změny, je nutné zastavit ladění a restartovat s novou verzí kódu.

## <a name="supported-changes-to-code"></a>Podporované změny kódu

V následující tabulce jsou uvedeny změny, které mohou být provedeny v C# a Visual Basic kódu během relace ladění, aniž by bylo nutné relaci restartovat.

|Jazykové prvky/funkce|Podporovaná operace Edit|Omezení|
|-|-|-|
|Typy|Přidat metody, pole, konstruktory, et al|[Ano](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterátory|Přidat nebo upravit|Ne|
|výrazy Async/await|Přidat nebo upravit|[Ano](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Dynamické objekty|Přidat nebo upravit|Ne|
|lambda – výrazy|Přidat nebo upravit|[Ano](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Výrazy LINQ|Přidat nebo upravit|[Stejné jako výrazy lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Novější funkce jazyka, jako je například interpolace řetězců a podmíněné operátory null, jsou obecně podporovány funkcí upravit a pokračovat. Nejaktuálnější informace najdete na stránce s [podporovanými úpravami](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) .

## <a name="unsupported-changes-to-code"></a>Nepodporované změny kódu
 Následující změny nelze použít pro C# a Visual Basic kódu během relace ladění:

- Změny aktuálního příkazu nebo jakéhokoli jiného aktivního příkazu.

     Aktivní příkazy zahrnují všechny příkazy ve funkcích v zásobníku volání, které byly volány pro získání na aktuální příkaz.

     Aktuální příkaz je označen žlutým pozadím v okně zdroje. Další aktivní příkazy jsou označeny šedým pozadím a jsou jen pro čtení. Tyto výchozí barvy lze změnit v dialogovém okně **Možnosti** .

- V následující tabulce jsou uvedeny nepodporované změny kódu podle prvku jazyka.

|Jazykové prvky/funkce|Nepodporovaná operace Edit|
|-|-|
|Všechny elementy kódu|Měníte|
|Obory názvů|Přidat|
|Obory názvů, typy, členy|Odstranit|
|Obecné typy|Přidat nebo upravit|
|Rozhraní|Modify|
|Typy|Přidat abstraktní nebo virtuální člen, přidat přepsání (viz [Podrobnosti](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Typy|Přidat destruktor|
|Členové|Úprava člena odkazujícího na vložený definiční typ|
|Členové|Úprava statického člena poté, co byl již otevřen spuštěním kódu|
|Členové (Visual Basic)|Úprava člena pomocí příkazu Error nebo Resume|
|Členové (Visual Basic)|Úprava člena obsahujícího agregační klauzuli, Group by, Simple JOIN nebo Group Join join klauzule dotazu LINQ|
|Metody|Úprava podpisů|
|Metody|Nastavit abstraktní metodu jako neabstraktní přidáním těla metody|
|Metody|Odstranit tělo metody|
|Atributy|Přidat nebo upravit|
|Události nebo vlastnosti|Úprava parametru typu, základního typu, typu delegáta nebo návratového typu |
|Operátory nebo indexery|Úprava parametru typu, základního typu, typu delegáta nebo návratového typu |
|catch – bloky|Upravit, když obsahuje aktivní příkaz|
|bloky try-catch-finally|Upravit, když obsahuje aktivní příkaz|
|using – příkazy|Přidat|
|asynchronní metody/výrazy lambda|Úprava asynchronní metody nebo výrazu lambda v projektu cílících na .NET Framework 4 a nižší (viz [Podrobnosti](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterátory|Úprava iterátoru v projektu cílící na .NET Framework 4 a nižší (viz [Podrobnosti](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Nebezpečný kód
 Změny v nebezpečném kódu mají stejná omezení jako změny v bezpečném kódu s jedním dalším omezením: příkaz Upravit a pokračovat nepodporuje změny nezabezpečeného kódu, který ukončuje v rámci metody, která obsahuje `stackalloc` operátor.

## <a name="unsupported-app-scenarios"></a>Nepodporované scénáře aplikací

Mezi nepodporované aplikace a platformy patří ASP.NET 5, Silverlight 5 a Windows 8.1.

> [!NOTE]
> Mezi podporované aplikace patří UWP ve Windows 10 a aplikace x86 a x64, které cílí na .NET Framework 4,6 Desktop nebo novějších verzích (.NET Framework je jenom verze desktopu).

## <a name="unsupported-scenarios"></a>Nepodporované scénáře
 Úpravy a pokračování nejsou k dispozici v následujících scénářích ladění:

- Ladění ve smíšeném režimu (nativní/spravované)

- Ladění SQL.

- Ladění výpisu nástroje Dr. Watson.

- Ladění vložené aplikace modulu runtime.

- Ladění aplikace pomocí příkazu připojit k procesu (**ladění > připojit k procesu**) místo spuštění aplikace výběrem možnosti **Spustit** v nabídce **ladění** .

- Ladění optimalizovaného kódu.

- Ladění staré verze kódu po neúspěšném sestavení nové verze z důvodu chyb sestavení.

## <a name="see-also"></a>Viz také
- [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Postupy: Použití operace Upravit a pokračovat (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)