---
title: FxCop kód analýzy a FxCop analyzátory
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431362"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Nejčastější dotazy týkající se analyzátorů FxCop a FxCop

To může být trochu matoucí pochopit rozdíly mezi staršífxcop a FxCop analyzátory. Tento článek si klade za cíl řešit některé z otázek, které by mohly mít.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Jaký je rozdíl mezi staršími analyzátory FxCop a FxCop?

Starší FxCop spouští analýzu po sestavení na kompilovaném sestavení. Běží jako samostatný spustitelný soubor s názvem **FxCopCmd.exe**. FxCopCmd.exe načte zkompilované sestavení, spustí analýzu kódu a pak hlásí výsledky (nebo *diagnostiku).*

Analyzátory FxCop jsou založeny na platformě kompilátoru .NET ("Roslyn"). Můžete [je nainstalovat jako balíček NuGet,](install-fxcop-analyzers.md#nuget-package) na který odkazuje projekt nebo řešení. Analyzátory FxCop spouštějí analýzu založenou na zdrojovém kódu během provádění kompilátoru. FxCop analyzátory jsou hostovány v rámci procesu kompilátoru, buď **csc.exe** nebo **vbc.exe**, a spustit analýzu při sestavení projektu. Výsledky analyzátoru jsou hlášeny spolu s výsledky kompilátoru.

> [!NOTE]
> Můžete také [nainstalovat analyzátory FxCop jako rozšíření sady Visual Studio](install-fxcop-analyzers.md#vsix). V tomto případě analyzátory spustit při psaní v editoru kódu, ale nespustí v době sestavení. Pokud chcete spustit analyzátory FxCop jako součást průběžné integrace (CI), nainstalujte je jako balíček NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Spouštět příkaz Analýza kódu spouštět analyzátory FxCop?

Před vydáním Visual Studia 2019 16.5, když vyberete **Analyzovat** > **analýzu kódu spuštění**, provede starší analýzu. Spuštění visual studio 2019 16.5, **spustit analýzu kódu** možnost nabídky spustí analyzátory založené na Roslyn pro vybraný projekt nebo řešení. Pokud jste nainstalovali analyzátory FxCop založené na Roslynu, byly by také provedeny. Další informace naleznete v [tématu How to: Run Code Analysis Manually for Managed Code](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Spouštějí analyzátory projektu msbuild RunCodeAnalysis?

Ne. **Vlastnost RunCodeAnalysis** v souboru projektu (například *.csproj*) se používá pouze ke spuštění starší fxcop. Spustí úlohu msbuild po sestavení, která vyvolá soubor **FxCopCmd.exe**.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Tak jak mohu spustit FxCop analyzátory pak?

Chcete-li spustit analyzátory FxCop, [nejprve nainstalujte balíček NuGet](install-fxcop-analyzers.md) pro ně. Potom vytvořte projekt nebo řešení z visual studia nebo pomocí msbuild. Upozornění a chyby, které analyzátory FxCop generovat se zobrazí v **seznamu chyb** nebo příkazového okna.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Dostávám varování CA0507 i poté, co jsem nainstaloval FxCop analyzátory NuGet balíček

Pokud jste nainstalovali FxCop analyzátory, ale i nadále dostat varování CA0507 **""Run Code Analysis" byl zastaralá ve prospěch FxCop analyzátory, které běží během sestavení"**, možná budete muset nastavit **RunCodeAnalysis** msbuild vlastnost v [souboru projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file) na **false**. V opačném případě starší analýzy se spustí po každém sestavení.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Jaká pravidla byla přenesena na analyzátory FxCop?

Informace o tom, která starší pravidla analýzy byla přenesena do [analyzátorů FxCop](install-fxcop-analyzers.md), naleznete v [tématu Stav portu pravidla Fxcop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Upozornění analýzy kódu jsou považována za chyby

Pokud váš projekt používá možnost sestavení k použití upozornění jako chyby, fxcop analyzátor upozornění se může zobrazit jako chyby. Chcete-li zabránit tomu, aby se upozornění na analýzu kódu považovala za chyby, postupujte podle pokynů v [nejčastějších dotazech](../code-quality/analyzers-faq.md#treat-warnings-as-errors)k analýze kódu .

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů platformy kompilátoru .NET](roslyn-analyzers-overview.md)
- [Migrace do analyzátorů FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Instalace analyzátorů FxCop](install-fxcop-analyzers.md)
