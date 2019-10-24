---
title: Použití Clang-uklizený v aplikaci Visual Studio
ms.date: 10/04/2019
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.workload:
- cplusplus
ms.openlocfilehash: e226ac6c83839474b9d8ac6be7fb57e376de4a4f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745982"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Použití Clang-uklizený v aplikaci Visual Studio

Analýza kódu nativně podporuje [Clang-uklizený](https://clang.llvm.org/extra/clang-tidy/) pro projekty MSBuild i cmake bez ohledu na to, jestli používáte sady nástrojů pro CLANG nebo MSVC. Clang-uklizený kontroly mohou běžet jako součást analýzy kódu na pozadí, zobrazují se jako upozornění v editoru (vlnovky) a zobrazují se v Seznam chyb.

Aby bylo možné používat Clang-uklizený, musí býtC++ nainstalována součást Clang Tools for Windows prostřednictvím instalační program pro Visual Studio.

Clang-uklizený je výchozím nástrojem analýzy při použití sady nástrojů LLVM/Clang-CL, která je dostupná jak v MSBuild, tak i v CMaki. Můžete ji nakonfigurovat tak, aby běžela souběžně, nebo aby při použití sady nástrojů MSVC používala standardní prostředí pro analýzu kódu; Pokud používáte sadu nástrojů Clang-CL, Microsoft Code Analysis nebude k dispozici.

Clang-uklizený se spouští po úspěšné kompilaci; Možná budete muset vyřešit chyby zdrojového kódu a získat výsledky Clang-uklizený.


## <a name="msbuild"></a>MSBuild

Clang-uklizený můžete nakonfigurovat tak, aby běžela jako součást analýzy kódu a sestavení pod stránkou**obecné**  >  pro **analýzu kódu** v projektu okno Vlastnosti. Možnosti pro konfiguraci tohoto nástroje najdete v podnabídce Clang-uklizený.

Další informace naleznete v tématu [Postupy: nastavení vlastností analýzy kódu pro projekty C/C++ ](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

V projektech CMake můžete nakonfigurovat kontroly Clang-uklizený v rámci `CMakeSettings.json`. Po otevření klikněte na Upravit JSON v pravém horním rohu editoru nastavení projektu CMake. Rozpoznávají se tyto klíče:

- `enableMicrosoftCodeAnalysis`: povolí analýzu kódu společnosti Microsoft.
- `enableClangTidyCodeAnalysis`: povoluje analýzu Clang-uklizený.
- `clangTidyChecks`: Konfigurace Clang-uklizený zadaná jako seznam oddělený čárkami, tj. kontroly, které mají být povoleny nebo zakázány.

Pokud není zadána žádná z možností "Enable", sada Visual Studio vybere Nástroj pro analýzu, který odpovídá použité sadě nástrojů platformy.

## <a name="warning-display"></a>Zobrazení upozornění

Clang-uklizený spustí výsledek v upozorněních zobrazených v Seznam chyb a jako editor vlnovek pod relevantními oddíly kódu. Použijte sloupec Category v Seznam chyb k řazení a uspořádání upozornění Clang-uklizený. Můžete nakonfigurovat upozornění v editoru tak, že v nabídce **nástroje**  > **Možnosti**zakážete nastavení zakázat vlnovky analýzy kódu.

## <a name="clang-tidy-configuration"></a>Konfigurace Clang-uklizený

Můžete nakonfigurovat kontroly, které Clang-uklizený spouští v rámci sady Visual Studio prostřednictvím možnosti **Clang-uklizený Checks** . Tento vstup je poskytován argumentem **--Checks** nástroje. Do vlastních souborů **. Clang-uklizený** je možné zahrnout jakoukoli další konfiguraci. Další podrobnosti najdete v [dokumentaci k Clang-uklizený na LLVM.org](https://clang.llvm.org/extra/clang-tidy/) .

## <a name="see-also"></a>Viz také:

- [Podpora Clang/LLVM pro projekty MSBuild](https://aka.ms/cpp/clangmsbuild)
- [Podpora Clang/LLVM pro projekty CMake](https://aka.ms/cpp/clangcmake)
