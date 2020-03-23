---
title: Řešení sestavení v době návrhu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69f5ba2627e2d659665fa0bd3fbf706f9cad5573
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632560"
---
# <a name="resolve-assemblies-at-design-time"></a>Řešení sestavení v době návrhu

Když přidáte odkaz na sestavení prostřednictvím karty **.NET** dialogového okna **Přidat odkaz,** odkaz odkazuje na zprostředkující referenční sestavení; to znamená sestavení, které obsahuje všechny informace o typu a podpisu, ale nemusí nutně obsahovat žádný kód. Karta **.NET** uvádí referenční sestavení, která odpovídají sestavením za běhu v rozhraní .NET Framework. Kromě toho uvádí referenční sestavení, která odpovídají sestavení za běhu v registrovaných složek AssemblyFoldersEx, které jsou používány třetími stranami.

## <a name="multi-targeting"></a>Vícenásobné cílení

 Visual Studio umožňuje cílit na verze rozhraní .NET Framework, které běží na více verzích rozhraní .NET Framework. Po vydání nové verze rozhraní .NET Framework lze rozhraní nainstalovat pomocí balíčku cílení a automaticky se zobrazí jako cíl v sadě Visual Studio.

## <a name="how-type-resolution-works"></a>Jak funguje rozlišení textu

 V době běhu CLR řeší typy v sestavení při pohledu do GAC, *bin* adresáře a v jakékoli sondování cesty. K tomuto účelu se používá zavaděč syntézy. Jak ale zavaděč syntézy ví, kde má hledat? Záleží na rozlišení provedené v době návrhu, kdy je aplikace vytvořena.

 Během sestavování přeloží kompilátor typy aplikací pomocí referenčních sestavení. V rozhraní .NET Framework verze 2.0, 3.0, 3.5, 4, 4.5 a 4.5.1 se referenční sestavení nainstalují při instalaci rozhraní .NET Framework.

 Referenční sestavení jsou poskytována v sadě cílů, která je dodávána spolu s konkrétní verzí sady SDK rozhraní .NET Framework. Rozhraní samotné poskytuje pouze sestavení modulu runtime. Při sestavování aplikací je nutné nainstalovat jak rozhraní .NET Framework, tak i odpovídající sadu SDK pro rozhraní .NET Framework.

 Při cílení na určité rozhraní .NET Framework přeloží systém sestavení všechny typy pomocí referenčních sestavení v sadě cílů. V době běhu fúzní zavaděč řeší tyto stejné typy na sestavení za běhu, které jsou obvykle umístěny v GAC.

 Nejsou-li referenční sestavení dostupná, přeloží systém typy sestavení pomocí sestavení modulu runtime. Vzhledem k tomu, že sestavení za běhu v GAC nejsou rozlišována dílčími čísly verzí, je možné, že řešení bude provedeno nesprávnésestavení. K tomu může dojít například při odkazování na metodu, která je představena v rozhraní .NET Framework verze 3.5, ale cíleno je na verzi 3.0. Sestavení proběhne úspěšně a aplikace bude spuštěna na počítači, na kterém je prováděno sestavení, ale nasazení této aplikace selže na počítači, který nemá nainstalovánu verzi 3.5.

 Balíček cílení, který je nyní dodáván s sadou .NET Framework SDK, obsahuje seznam všech sestavení runtime v této verzi rozhraní Framework, nazývaný seznam redistribuce (redist), což znemožňuje systému sestavení vyřešit typy proti nesprávnému verzi sestavení.

## <a name="see-also"></a>Viz také
- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
