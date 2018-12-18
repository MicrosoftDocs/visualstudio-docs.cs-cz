---
title: Překlad sestavení v době návrhu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc10169ac07efdeded41a9bb2990bdc206a17435
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224650"
---
# <a name="resolving-assemblies-at-design-time"></a>Překlad sestavení v době návrhu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Po přidání odkazu na sestavení pomocí karty .NET dialogového okna Přidat odkaz bude odkaz ukazovat na zprostředkující referenční sestavení, což je sestavení, které obsahuje veškeré informace o typech a podpisech, ale nezbytně nemusí obsahovat žádný kód. Karta .NET obsahuje referenční sestavení, která odpovídají sestavením modulu runtime v rozhraní .NET Framework. Kromě toho obsahují referenční sestavení, jež odpovídají sestavením modulu runtime v registrovaných složkách AssemblyFoldersEx, které jsou používány třetími stranami.  
  
## <a name="multi-targeting"></a>Cílení na více verzí  
 Aplikace [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] umožňuje používat cílové verze rozhraní .NET Framework, které spouští modul CLR (Common Language Runtime) verze 2.0 nebo verze 4. Jedná se o rozhraní .NET Framework verze 2.0, 3.0, 3.5, 4, 4.5 a 4.5.1 a verze Silverlight 1.0, 2.0 a 3.0. Je-li vydána nová verze rozhraní .NET Framework založeného na modulu CLR verze 2.0 nebo verze 4, může být rozhraní nainstalováno pomocí sady cílů a automaticky zobrazeno jako cíl v sadě Visual Studio.  
  
## <a name="how-type-resolution-works"></a>Principy překladu typů  
 V době běhu překládá CLR typy v sestavení náhledem do GAC do adresáře bin a do všech definovaných cest. K tomuto účelu se používá zavaděč syntézy. Jak ale zavaděč syntézy ví, kde má hledat? To záleží na rozhodnutí, které je provedeno v době návrhu, při sestavování aplikace.  
  
 Během sestavování přeloží kompilátor typy aplikací pomocí referenčních sestavení. V rozhraní .NET Framework verze 2.0, 3.0, 3.5, 4, 4.5 a 4.5.1 jsou referenční sestavení nainstalována spolu s rozhraním .NET Framework.  
  
 Referenční sestavení jsou poskytována v sadě cílů, která je dodávána spolu s konkrétní verzí sady SDK rozhraní .NET Framework. Rozhraní samotné poskytuje pouze sestavení modulu runtime. Při sestavování aplikací je nutné nainstalovat jak rozhraní .NET Framework, tak i odpovídající sadu SDK pro rozhraní .NET Framework.  
  
 Při cílení na určité rozhraní .NET Framework přeloží systém sestavení všechny typy pomocí referenčních sestavení v sadě cílů. Zavaděč syntézy přeloží tyto totožné typy v době běhu na sestavení modulu runtime, která se obvykle nachází v globální mezipaměti sestavení (GAC).  
  
 Nejsou-li referenční sestavení dostupná, přeloží systém typy sestavení pomocí sestavení modulu runtime. Protože se sestavení modulu runtime v rámci GAC nerozlišují čísly podverze, je možné, že bude proveden překlad na špatné sestavení. K tomu může dojít například při odkazování na metodu, která je představena v rozhraní .NET Framework verze 3.5, ale cíleno je na verzi 3.0. Sestavení proběhne úspěšně a aplikace bude spuštěna na počítači, na kterém je prováděno sestavení, ale nasazení této aplikace selže na počítači, který nemá nainstalovánu verzi 3.5.  
  
 Sada cílů, která je nyní dodávána se sadou SDK rozhraní .NET Framework, obsahuje seznam všech sestavení modulu runtime, která jsou zahrnuta v této konkrétní verzi rozhraní .NET Framework, s názvem seznam redistribuce (redist). To znemožňuje systému sestavení přeložit typy vůči špatné verzi sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Rozšířené koncepty](../msbuild/msbuild-advanced-concepts.md)



