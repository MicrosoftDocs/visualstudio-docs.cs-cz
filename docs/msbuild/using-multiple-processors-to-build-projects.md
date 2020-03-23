---
title: Použití více procesorů k vytváření projektů | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: f5dc62112324f7ad19c47b346ac8c1e3f86570b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631299"
---
# <a name="use-multiple-processors-to-build-projects"></a>Použití více procesorů k vytváření projektů

Nástroj MSBuild může využívat výhod systémů s více procesory nebo procesorů s více jádry. Pro každý dostupný procesor je vytvořen samostatný proces sestavení. Pokud má systém například čtyři procesory, jsou vytvořeny čtyři procesy sestavení. MSBuild můžete zpracovat tyto sestavení současně a proto celkový čas sestavení je snížena. Paralelní sestavení však zavádí některé změny v tom, jak dochází k procesům sestavení. V tomto tématu jsou dané změny popsány.

## <a name="project-to-project-references"></a>Odkazy na projekt-projekt

 Když Microsoft Build Engine narazí na odkaz projekt projektu (P2P) při použití paralelní sestavení k sestavení projektu, vytvoří odkaz pouze jednou. Obsahují-li stejný P2P odkaz dva projekty, nedojde k opětovnému sestavení odkazu pro každý projekt. Místo toho se jádro sestavení vrátí na stejný P2P odkaz obou projektů, které na něm závisí. Budoucím požadavkům relace stejného cíle je poskytnut stejný P2P odkaz.

## <a name="cycle-detection"></a>Detekce cyklu

 Funkce detekce cyklu stejné jako v MSBuild 2.0, s tím rozdílem, že nyní MSBuild můžete hlásit detekci cyklu v jiném čase nebo v sestavení.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Chyby a výjimky během paralelních sestavení

 V paralelních sestaveních se mohou chyby a výjimky vyskytovat v odlišnou dobu, než jak je tomu u neparalelních sestavení. Nebo nedojde-li k sestavení projektu, sestavování jiného projektu pokračuje. MSBuild nezastaví sestavení projektu, který je vytváření paralelně s tím, který selhal. Ostatní projekty pokračovat v sestavení, dokud se jim buď podaří nebo nepodaří. Pokud však bylo povoleno nastavení <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, nedojde k zastavení žádných sestavení dokonce ani při výskytu chyby.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++ projekt (.vcxproj) a řešení (.sln) soubory

 Oba projekty Jazyka C++ (*.vcxproj*) a soubory řešení (*.sln)* mohou být předány [úkolu MSBuild](../msbuild/msbuild-task.md). Pro projekty jazyka C++ je volána aplikace VCWrapperProject a potom je vytvořen interní projekt MSBuild. Pro řešení jazyka C++ je vytvořen SolutionWrapperProject a potom je vytvořen interní projekt MSBuild. V obou případech je výsledný projekt zpracován stejně jako jakýkoli jiný projekt MSBuild.

## <a name="multi-process-execution"></a>Víceprocesové spuštění

 Téměř všechny činnosti týkající se sestavení vyžadují, aby aktuální adresář zůstal neměnný po celou dobu procesu sestavení, protože jen tak se zabrání chybám souvisejícím s umístěním. Proto projekty nelze spustit v různých vláknech v MSBuild, protože by způsobit více adresářů, které mají být vytvořeny.

 Chcete-li se tomuto problému vyhnout, ale stále povolit sestavení s více procesory, MSBuild používá "izolace procesu." Pomocí izolace procesu MSBuild můžete `n` vytvořit `n` maximální procesy, kde se rovná počtu procesorů dostupných v systému. Například pokud MSBuild vytvoří řešení v systému, který má dva procesory, pak jsou vytvořeny pouze dva procesy sestavení. Tyto procesy jsou znovu použity k sestavení všech projektů v řešení.

## <a name="see-also"></a>Viz také

- [Paralelní vytváření více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
