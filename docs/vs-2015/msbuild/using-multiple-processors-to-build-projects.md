---
title: Použití více procesorů k sestavení projektů | Dokumentace Microsoftu
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
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b873b8ab1668ea2fea3b3bf0487339a86c9ffe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199911"
---
# <a name="using-multiple-processors-to-build-projects"></a>Použití více procesorů k sestavení projektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Nástroj MSBuild může využívat výhod systémů s více procesory nebo procesorů s více jádry. Pro každý dostupný procesor je vytvořen samostatný proces sestavení. Pokud má systém například čtyři procesory, jsou vytvořeny čtyři procesy sestavení. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] může tato sestavení zpracovávat současně, a proto celkové snížit dobu sestavení. Paralelní sestavení však zavádí některé změny v tom, jak dochází k procesům sestavení. V tomto tématu jsou dané změny popsány.  
  
## <a name="project-to-project-references"></a>Odkazy typu projekt na projekt  
 Když [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] zjistí odkaz typu projekt projekt (P2P) při použití paralelních sestavení pro sestavení projektu, sestaví odkaz pouze jednou. Obsahují-li stejný P2P odkaz dva projekty, nedojde k opětovnému sestavení odkazu pro každý projekt. Místo toho se jádro sestavení vrátí na stejný P2P odkaz obou projektů, které na něm závisí. Budoucím požadavkům relace stejného cíle je poskytnut stejný P2P odkaz.  
  
## <a name="cycle-detection"></a>Zjišťování cyklů  
 Detekce cyklu funguje stejně jako fungovala v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0, kromě toho, že nyní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] můžete vykazovat zjištění cyklu v odlišnou dobu nebo v sestavení.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Chyby a výjimky během paralelního sestavení  
 V paralelních sestaveních se mohou chyby a výjimky vyskytovat v odlišnou dobu, než jak je tomu u neparalelních sestavení. Nebo nedojde-li k sestavení projektu, sestavování jiného projektu pokračuje. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] neukončí žádné sestavení projektu, které je sestavováno souběžně s tím, jež selhalo. Ostatní projekty pokračují až do jejich úspěch nebo neúspěch sestavení. Pokud však bylo povoleno nastavení <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, nedojde k zastavení žádných sestavení dokonce ani při výskytu chyby.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Soubory projektu (.vcproj) a řešení (.sln) Visual C++  
 Obě [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projekty (.vcproj) a soubory řešení (.sln) může být předán [úlohy nástroje MSBuild](../msbuild/msbuild-task.md). Pro [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektů, se nazývá VCWrapperProject a potom interní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vytvoření projektu. Pro [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] řešení, vytvoření SolutionWrapperProject a následně interní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vytvoření projektu. V obou případech je s výsledným projektem zacházeno stejně jako se všemi ostatními projekty nástroje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="multi-process-execution"></a>Provádění ve více procesech  
 Téměř všechny činnosti týkající se sestavení vyžadují, aby aktuální adresář zůstal neměnný po celou dobu procesu sestavení, protože jen tak se zabrání chybám souvisejícím s umístěním. Z toho důvodu nelze projekty v rámci nástroje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] spouštět v různých vláknech, jelikož by to mohlo vést k vytvoření více adresářů.  
  
 Nástroj [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] se tomuto problému vyhýbá a při tom povoluje sestavení s více procesory pomocí „izolace procesů“. Pomocí izolace procesů může nástroj [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vytvořit maximálně `n` procesů, kde `n` se rovná počtu procesorů, které jsou v systému k dispozici. Pokud například nástroj [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sestaví řešení v systému, který má dva procesory, budou vytvořeny pouze dva procesy sestavení. Tyto procesy jsou znovu použity k sestavení všech projektů v řešení.  
  
## <a name="see-also"></a>Viz také  
 [Sestavování více projektů současně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)



