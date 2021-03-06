---
title: Modul CLR (Common Language Runtime) a vyhodnocení výrazu | Microsoft Docs
description: Přečtěte si, jak modul CLR (Common Language Runtime) spolupracuje s ladicím modulem a jak integrovat proprietární programovací jazyk do integrovaného vývojového prostředí sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35ddc218d0e9499253269a12687fa89122cfe007
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055008"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>CLR (Common Language Runtime) a vyhodnocení výrazu
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Kompilátory, jako je například Visual Basic a C# (vyslovované v jazyce C-Sharp), které cílí na modul CLR (Common Language Runtime), tvoří jazyk MSIL (Microsoft Intermediate Language), který je později zkompilován do nativního kódu. Modul CLR poskytuje ladicí modul (DE) pro ladění výsledného kódu. Pokud máte v úmyslu integrovat svůj proprietární programovací jazyk do integrovaného vývojového prostředí sady Visual Studio, můžete se rozhodnout kompilovat do jazyka MSIL, a proto nebude nutné psát vlastní DE. Budete však muset napsat vyhodnocovací filtr výrazů (EE), který dokáže vyhodnotit výrazy v kontextu vašeho programovacího jazyka.

## <a name="discussion"></a>Diskuse
 Výrazy jazyka počítače jsou všeobecně analyzovány tak, aby vytvořily sadu datových objektů a sadu operátorů používaných k manipulaci s nimi. Například výraz "A + B" může být analyzován pro použití operátoru sčítání (+) k datovým objektům "A" a "B" pravděpodobně v důsledku výsledku v jiném datovém objektu. Celková sada datových objektů, operátorů a jejich přidružení jsou nejčastěji zastoupena v programu jako stromové struktury s operátory v uzlech stromu a objekty dat v větvích. Výraz, který byl rozdělen do stromu formuláře, se často označuje jako analyzovaný strom.

 Po analýze výrazu se zavolá poskytovatel symbolů (SP), který vyhodnotí každý datový objekt. Například pokud je "A" definováno jak ve více než jedné metodě, otázka "kterou?" musí být zodpovězen před tím, než se dá zjistit hodnota. Odpověď vrácená aktualizací SP je něco jako "třetí položka na pátém bloku zásobníku" nebo "A", která je 50 bajtů po spuštění statické paměti přidělené této metodě. "

 Kromě vystavení MSIL pro samotný program mohou kompilátory CLR také vytvořit velmi popisné ladicí informace, které jsou zapsány do souboru databáze programu (*PDB*). Pokud kompilátor pro vlastní jazyk vytváří informace o ladění ve stejném formátu jako kompilátory CLR, je možné, že je v rámci modulu CLR pro daný jazyk identifikovány pojmenované datové objekty. Po zjištění pojmenovaného datového objektu použije parametr EE objekt Binder k přidružení (nebo svázání) datového objektu k oblasti paměti, která obsahuje hodnotu tohoto objektu. DE pak může získat nebo nastavit novou hodnotu pro datový objekt.

 Proprietární kompilátor může poskytnout ladicí informace CLR voláním `ISymbolWriter` rozhraní (které je definováno v .NET Framework v oboru názvů `System.Diagnostics.SymbolStore` ). Pomocí kompilace do jazyka MSIL a psaní ladicích informací prostřednictvím těchto rozhraní může proprietární kompilátor použít CLR DE a SP. To významně zjednodušuje integraci vlastního jazyka do integrovaného vývojového prostředí (IDE) sady Visual Studio.

 Když CLR DE zavolá proprietární EE za účelem vyhodnocení výrazu, DE doplní rozhraní EE s rozhraními do objektu SP a pořadače. Proto zápis ladicího stroje založeného na CLR znamená, že je potřeba pouze implementovat odpovídající rozhraní vyhodnocovacího filtru výrazů. CLR se postará o vazbu a zpracování symbolů za vás.

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
