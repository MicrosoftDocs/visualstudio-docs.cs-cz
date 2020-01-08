---
title: Použití více procesorů k sestavení projektů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd377318d92989f7e1341d166b2ca3d3978a148d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595237"
---
# <a name="use-multiple-processors-to-build-projects"></a>Použití více procesorů k sestavení projektů
Nástroj MSBuild může využívat výhod systémů s více procesory nebo procesorů s více jádry. Pro každý dostupný procesor je vytvořen samostatný proces sestavení. Pokud má systém například čtyři procesory, jsou vytvořeny čtyři procesy sestavení. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mohou současně zpracovat tato sestavení, a proto se zmenší celkový čas sestavení. Paralelní sestavení však zavádí některé změny v tom, jak dochází k procesům sestavení. V tomto tématu jsou dané změny popsány.

## <a name="project-to-project-references"></a>Odkazy z projektu na projekt
 Když [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] narazí na odkaz v rámci projektu na projekt (P2P), zatímco používá paralelní sestavení k sestavení projektu, sestaví odkaz pouze jednou. Obsahují-li stejný P2P odkaz dva projekty, nedojde k opětovnému sestavení odkazu pro každý projekt. Místo toho se jádro sestavení vrátí na stejný P2P odkaz obou projektů, které na něm závisí. Budoucím požadavkům relace stejného cíle je poskytnut stejný P2P odkaz.

## <a name="cycle-detection"></a>Detekce cyklu
 Detekce cyklu funguje stejně jako v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0, s tím rozdílem, že nyní [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] může vykazovat detekci cyklu v jinou dobu nebo v sestavení.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Chyby a výjimky během paralelních sestavení
 V paralelních sestaveních se mohou chyby a výjimky vyskytovat v odlišnou dobu, než jak je tomu u neparalelních sestavení. Nebo nedojde-li k sestavení projektu, sestavování jiného projektu pokračuje. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nezastaví žádné sestavení projektu, které se sestavuje paralelně s rozhraním, které selhalo. Ostatní projekty budou pokračovat v sestavování, dokud nebudou úspěšné nebo neúspěšné. Pokud však bylo povoleno nastavení <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, nedojde k zastavení žádných sestavení dokonce ani při výskytu chyby.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++soubory projektu (. vcxproj) a řešení (. sln)
 Do [úlohy MSBuild](../msbuild/msbuild-task.md)lze předat jak projekty [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] ( *. vcxproj*), tak soubory řešení ( *. sln*). Pro [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekty se zavolá VCWrapperProject a pak se vytvoří interní [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt. Pro [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] řešení se vytvoří SolutionWrapperProject a pak se vytvoří interní [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt. V obou případech je s výsledným projektem zacházeno stejně jako se všemi ostatními projekty nástroje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="multi-process-execution"></a>Provádění více procesů
 Téměř všechny činnosti týkající se sestavení vyžadují, aby aktuální adresář zůstal neměnný po celou dobu procesu sestavení, protože jen tak se zabrání chybám souvisejícím s umístěním. Z toho důvodu nelze projekty v rámci nástroje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] spouštět v různých vláknech, jelikož by to mohlo vést k vytvoření více adresářů.

 Nástroj [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se tomuto problému vyhýbá a při tom povoluje sestavení s více procesory pomocí „izolace procesů“. Pomocí izolace procesů může nástroj [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vytvořit maximálně `n` procesů, kde `n` se rovná počtu procesorů, které jsou v systému k dispozici. Pokud například nástroj [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sestaví řešení v systému, který má dva procesory, budou vytvořeny pouze dva procesy sestavení. Tyto procesy jsou znovu použity k sestavení všech projektů v řešení.

## <a name="see-also"></a>Viz také:
- [Paralelní sestavení více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
