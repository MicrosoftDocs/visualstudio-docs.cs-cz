---
title: Řešení sestavení v době návrhu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 131cc61614c9f3e814cca5bcbc0ff6db303414cf
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253758"
---
# <a name="resolve-assemblies-at-design-time"></a>Přeložit sestavení v době návrhu
Přidáte-li odkaz na sestavení prostřednictvím karty **.NET** dialogového okna **Přidat odkaz** , odkaz odkazuje na sestavení zprostředkujícího odkazu; To znamená, že sestavení, které obsahuje všechny informace o typu a podpisu, ale nutně neobsahuje žádný kód. Karta **.NET** obsahuje seznam referenčních sestavení, která odpovídají sestavením modulu runtime v .NET Framework. Kromě toho obsahuje referenční sestavení, která odpovídají sestavením modulu runtime v registrovaných složkách AssemblyFoldersEx, které používají třetí strany.

## <a name="multi-targeting"></a>Cílení na více platforem
 Aplikace [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] umožňuje používat cílové verze rozhraní .NET Framework, které spouští modul CLR (Common Language Runtime) verze 2.0 nebo verze 4. Mezi tyto verze patří .NET Framework verze 2,0, 3,0, 3,5, 4, 4,5 a 4.5.1 a verze programu Silverlight, 1,0, 2,0 a 3,0. Je-li vydána nová verze rozhraní .NET Framework založeného na modulu CLR verze 2.0 nebo verze 4, může být rozhraní nainstalováno pomocí sady cílů a automaticky zobrazeno jako cíl v sadě Visual Studio.

## <a name="how-type-resolution-works"></a>Jak řešení typu funguje
 V době běhu modul CLR vyřeší typy v sestavení tak, že prohlíží v mezipaměti GAC, adresáři *bin* a v rámci všech cest zjišťování. K tomuto účelu se používá zavaděč syntézy. Jak ale zavaděč syntézy ví, kde má hledat? Závisí na řešení provedeném v době návrhu, při sestavení aplikace.

 Během sestavování přeloží kompilátor typy aplikací pomocí referenčních sestavení. V .NET Framework verzích 2,0, 3,0, 3,5, 4, 4,5 a 4.5.1, se referenční sestavení nainstalují při instalaci .NET Framework.

 Referenční sestavení jsou poskytována v sadě cílů, která je dodávána spolu s konkrétní verzí sady SDK rozhraní .NET Framework. Rozhraní samotné poskytuje pouze sestavení modulu runtime. Při sestavování aplikací je nutné nainstalovat jak rozhraní .NET Framework, tak i odpovídající sadu SDK pro rozhraní .NET Framework.

 Při cílení na určité rozhraní .NET Framework přeloží systém sestavení všechny typy pomocí referenčních sestavení v sadě cílů. V době spuštění překládá zavaděč Fusion stejné typy na sestavení modulu runtime, která jsou obvykle umístěna v mezipaměti GAC.

 Nejsou-li referenční sestavení dostupná, přeloží systém typy sestavení pomocí sestavení modulu runtime. Vzhledem k tomu, že běhová sestavení v mezipaměti GAC nejsou odlišena čísly podverze, je možné, že řešení bude provedeno na nesprávné sestavení. K tomu může dojít například při odkazování na metodu, která je představena v rozhraní .NET Framework verze 3.5, ale cíleno je na verzi 3.0. Sestavení proběhne úspěšně a aplikace bude spuštěna na počítači, na kterém je prováděno sestavení, ale nasazení této aplikace selže na počítači, který nemá nainstalovánu verzi 3.5.

 Sada targeting pack, která je nyní dodávána se sadou .NET Framework SDK, obsahuje seznam všech sestavení modulu runtime v této verzi rozhraní označovaného jako seznam Redistribuce (Redist), což znemožňuje systému sestavení překládat typy proti chybnému verze sestavení

## <a name="see-also"></a>Viz také:
- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)