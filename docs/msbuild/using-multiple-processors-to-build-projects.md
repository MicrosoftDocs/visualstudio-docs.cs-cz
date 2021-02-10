---
title: Použití více procesorů k sestavení projektů | Microsoft Docs
description: Naučte se, jak MSBuild využívá systémy, které mají více procesorů nebo jader, vytvoření samostatného procesu sestavení pro každý dostupný procesor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1560b40fe94af8dae5223981dd8e0c790320085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946368"
---
# <a name="use-multiple-processors-to-build-projects"></a>Použití více procesorů k sestavení projektů

Nástroj MSBuild může využívat výhod systémů s více procesory nebo procesorů s více jádry. Pro každý dostupný procesor je vytvořen samostatný proces sestavení. Pokud má systém například čtyři procesory, jsou vytvořeny čtyři procesy sestavení. Nástroj MSBuild může zpracovávat tato sestavení současně, a proto je celkový čas sestavení snížen. Paralelní sestavení však zavádí některé změny v tom, jak dochází k procesům sestavení. V tomto tématu jsou dané změny popsány.

## <a name="project-to-project-references"></a>Odkazy z projektu na projekt

 Když Microsoft Build Engine narazí na odkaz v rámci projektu na projekt (P2P), zatímco používá paralelní sestavení k sestavení projektu, sestaví odkaz pouze jednou. Obsahují-li stejný P2P odkaz dva projekty, nedojde k opětovnému sestavení odkazu pro každý projekt. Místo toho se jádro sestavení vrátí na stejný P2P odkaz obou projektů, které na něm závisí. Budoucím požadavkům relace stejného cíle je poskytnut stejný P2P odkaz.

## <a name="cycle-detection"></a>Detekce cyklu

 Detekce cyklu funguje stejně jako v MSBuild 2,0, s tím rozdílem, že nástroj MSBuild může zjistit detekci cyklu v jinou dobu nebo v sestavení.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Chyby a výjimky během paralelních sestavení

 V paralelních sestaveních se mohou chyby a výjimky vyskytovat v odlišnou dobu, než jak je tomu u neparalelních sestavení. Nebo nedojde-li k sestavení projektu, sestavování jiného projektu pokračuje. Nástroj MSBuild nezastaví žádné sestavení projektu, které se sestavuje paralelně s rozhraním, které selhalo. Ostatní projekty budou pokračovat v sestavování, dokud nebudou úspěšné nebo neúspěšné. Pokud však bylo povoleno nastavení <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, nedojde k zastavení žádných sestavení dokonce ani při výskytu chyby.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>Soubory projektů C++ (. vcxproj) a řešení (. sln)

 Do [úlohy MSBuild](../msbuild/msbuild-task.md)lze předat jak projekty C++ (*. vcxproj*), tak soubory řešení (*. sln*). Pro projekty v jazyce C++ se zavolá VCWrapperProject a pak se vytvoří interní projekt MSBuild. Pro řešení C++ je vytvořen SolutionWrapperProject a pak se vytvoří interní projekt MSBuild. V obou případech je výsledný projekt zpracován stejně jako jakýkoli jiný projekt MSBuild.

## <a name="multi-process-execution"></a>Provádění více procesů

 Téměř všechny činnosti týkající se sestavení vyžadují, aby aktuální adresář zůstal neměnný po celou dobu procesu sestavení, protože jen tak se zabrání chybám souvisejícím s umístěním. Proto projekty nelze v nástroji MSBuild spustit v různých vláknech, protože by mohlo dojít k vytvoření více adresářů.

 Chcete-li se tomuto problému vyhnout, ale přesto povolit sestavení s více procesory, nástroj MSBuild používá "izolaci procesů". Pomocí izolace procesů může MSBuild vytvořit maximálně `n` procesů, kde se `n` rovná počtu procesorů, které jsou v systému k dispozici. Například pokud MSBuild vytvoří řešení v systému, který má dva procesory, vytvoří se pouze dva procesy sestavení. Tyto procesy jsou znovu použity k sestavení všech projektů v řešení.

## <a name="see-also"></a>Viz také

- [Paralelní sestavení více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
