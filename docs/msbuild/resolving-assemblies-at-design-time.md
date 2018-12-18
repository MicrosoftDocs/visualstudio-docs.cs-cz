---
title: Překlad sestavení v době návrhu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad24bcf461dab05444f0e26ffd4e0c826f3f2bed
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153459"
---
# <a name="resolve-assemblies-at-design-time"></a>Přeložit sestavení v době návrhu
Když přidáte odkaz na sestavení pomocí **.NET** karty **přidat odkaz** dialogové okno, odkaz odkazuje na zprostředkující referenční sestavení, což znamená, sestavení, která obsahuje všechny typ a informace o podpisu, ale nutně neobsahuje žádný kód. **.NET** karta obsahuje referenční sestavení, které odpovídají sestavením modulu runtime v rozhraní .NET Framework. Kromě toho obsahují referenční sestavení, které odpovídají sestavením modulu runtime v registrovaných složkách AssemblyFoldersEx, které jsou používány třetími stranami.  
  
## <a name="multi-targeting"></a>Cílení na více platforem  
 Aplikace [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] umožňuje používat cílové verze rozhraní .NET Framework, které spouští modul CLR (Common Language Runtime) verze 2.0 nebo verze 4. Tyto verze zahrnují rozhraní .NET Framework verze 2.0, 3.0, 3.5, 4, 4.5 a 4.5.1 a verze Silverlight 1.0, 2.0 a 3.0. Je-li vydána nová verze rozhraní .NET Framework založeného na modulu CLR verze 2.0 nebo verze 4, může být rozhraní nainstalováno pomocí sady cílů a automaticky zobrazeno jako cíl v sadě Visual Studio.  
  
## <a name="how-type-resolution-works"></a>Zadejte jak funguje překlad  
 V době běhu překládá CLR typy v sestavení podle v mezipaměti GAC, *bin* adresář a do všech definovaných cest. K tomuto účelu se používá zavaděč syntézy. Jak ale zavaděč syntézy ví, kde má hledat? To závisí na rozlišení provedeno v době návrhu, když je aplikace sestavena.  
  
 Během sestavování přeloží kompilátor typy aplikací pomocí referenčních sestavení. V rozhraní .NET Framework verze 2.0, 3.0, 3.5, 4, 4.5 a 4.5.1 referenční sestavení nainstalovat při instalaci rozhraní .NET Framework.  
  
 Referenční sestavení jsou poskytována v sadě cílů, která je dodávána spolu s konkrétní verzí sady SDK rozhraní .NET Framework. Rozhraní samotné poskytuje pouze sestavení modulu runtime. Při sestavování aplikací je nutné nainstalovat jak rozhraní .NET Framework, tak i odpovídající sadu SDK pro rozhraní .NET Framework.  
  
 Při cílení na určité rozhraní .NET Framework přeloží systém sestavení všechny typy pomocí referenčních sestavení v sadě cílů. Zavaděč syntézy přeloží tyto totožné typy v době běhu na sestavení modulu runtime, která se obvykle nachází v globální mezipaměti sestavení (GAC).  
  
 Nejsou-li referenční sestavení dostupná, přeloží systém typy sestavení pomocí sestavení modulu runtime. Protože sestavení modulu runtime v mezipaměti GAC nejsou odlišené čísly podverze, je možné, že bude proveden překlad na špatné sestavení. K tomu může dojít například při odkazování na metodu, která je představena v rozhraní .NET Framework verze 3.5, ale cíleno je na verzi 3.0. Sestavení proběhne úspěšně a aplikace bude spuštěna na počítači, na kterém je prováděno sestavení, ale nasazení této aplikace selže na počítači, který nemá nainstalovánu verzi 3.5.  
  
 Targeting pack, které je nyní součástí sady SDK rozhraní .NET Framework obsahuje seznam všech sestavení modulu runtime v této verzi rozhraní Framework, názvem seznam Redistribuce (redist) může znemožnit systému sestavení přeložit typy vůči chybného verze sestavení.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšířené koncepty](../msbuild/msbuild-advanced-concepts.md)