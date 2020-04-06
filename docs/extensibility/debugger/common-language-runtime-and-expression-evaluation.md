---
title: Běžný jazyk Runtime a vyhodnocení výrazu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739120"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Společné jazykové runtime a vyhodnocení výrazu
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Kompilátory, jako je například Visual Basic a C# (vyslovováno c-sharp), které se zaměřují na clr (Common Language Runtime), produkují Microsoft Intermediate Language (MSIL), který je později kompilován do nativního kódu. CLR poskytuje ladicí modul (DE) pro ladění výsledného kódu. Pokud máte v plánu integrovat proprietární programovací jazyk do ide sady Visual Studio, můžete se rozhodnout zkompilovat do MSIL a proto nebude muset psát vlastní DE. Budete však muset napsat vyhodnocení výrazu (EE), který je schopen vyhodnotit výrazy v kontextu programovacího jazyka.

## <a name="discussion"></a>Diskuse
 Výrazy jazyka počítače jsou obvykle analyzovány k vytvoření sady datových objektů a sady operátorů používaných k manipulaci s nimi. Například výraz "A +B" může být analyzována použít operátor sčítání (+) na datové objekty "A" a "B", což může mít za následek jiný datový objekt. Celková sada datových objektů, operátorů a jejich přidružení jsou nejčastěji reprezentovány v programu jako strom, s operátory v uzlech stromu a datových objektů na větvích. Výraz, který byl rozdělen do stromové formy, se často nazývá analyzovaný strom.

 Po analýzě výrazu je volána zprostředkovatel symbolu (SP) k vyhodnocení každého datového objektu. Například pokud "A" je definována jak ve více než jednu metodu, otázka "Které A?" musí být zodpovězena dříve, než lze zjistit hodnotu A. Odpověď vrácená SP je něco jako "Třetí položka na pátém rámci zásobníku" nebo "A, která je 50 bajtů za začátkem statické paměti přidělené této metodě."

 Kromě výroby MSIL pro samotný program mohou kompilátory CLR také vytvářet velmi popisné informace o ladění, které jsou zapsány do souboru DataBase programu (*.pdb*). Tak dlouho, dokud kompilátor proprietární jazyk vytváří ladicí informace ve stejném formátu jako kompilátory CLR, CLR SP je schopen identifikovat tento jazyk pojmenované datové objekty. Jakmile byl identifikován pojmenovaný datový objekt, EE používá objekt pořadače k přidružení (nebo svázání) datového objektu k oblasti paměti, která obsahuje hodnotu tohoto objektu. DE pak můžete získat nebo nastavit novou hodnotu pro datový objekt.

 Proprietární kompilátor může poskytnout informace o `ISymbolWriter` ladění CLR voláním rozhraní (které `System.Diagnostics.SymbolStore`je definováno v rozhraní .NET Framework v oboru názvů). Kompilací do MSIL a zápisem ladicích informací prostřednictvím těchto rozhraní může proprietární kompilátor použít CLR DE a SP. To značně zjednodušuje integraci proprietárního jazyka do rozhraní IDE sady Visual Studio.

 Když CLR DE volá proprietární EE k vyhodnocení výrazu, DE dodává EE s rozhraním SP a pořadače objektu. Proto psaní modulu ladění založené na CLR znamená, že je nutné pouze implementovat rozhraní vyhodnocení příslušné výraz; CLR se postará o vazbu a manipulaci se symboly za vás.

## <a name="see-also"></a>Viz také
- [Napsat vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
