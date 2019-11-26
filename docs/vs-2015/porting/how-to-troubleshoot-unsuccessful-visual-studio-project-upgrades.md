---
title: 'Postupy: řešení potíží s upgrady neúspěšný projekt | Dokumentace Microsoftu'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 16232a72cd37f8d1d68760f032b6050e0bdf74c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300355"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Postupy: Řešení potíží spojených s neúspěšným upgradem projektu sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Může se stát, že Visual Studio nemůže plně převést projekt ze starší verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pokud tipy v následujících částech nevyřeší váš konkrétní problém, může být možné najít další informace na [wikiwebu TechNet: vývojový portál](https://go.microsoft.com/fwlink/?LinkId=254808).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Projekt se nespustí, protože nebyly nalezeny soubory
 Soubor projektu obsahuje pevně zakódované cesty k souborům, které [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] používá ke spuštění projektu po stisknutí klávesy F5. Tyto cesty mohou být umístění devenv.exe a další požadované soubory. V upgradovaných verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]mohly být změny cest těchto souborů změněny.

#### <a name="to-resolve-incorrect-file-paths"></a>Chcete-li vyřešit nesprávné cesty k souborům

1. V textovém editoru otevřete soubor projektu.

2. Vyhledat cesty k souborům, které mohou být nesprávné, zejména ty, které obsahují číslo verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

3. Úprava cesty k souboru tak, aby ukazovaly na novou cíle.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Projekt sestavit, protože odkazy nejsou platné
 Pokud upgradujete [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete také upgradovat [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi. Pokud váš projekt obsahuje odkazy, které byly v novější verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ukončeny, nemusí se vyřešit správně. To je obzvláště nejspíš u odkazů, které obsahují čísla verzí, například `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Pokud má váš kód mnoho neplatných odkazů, nejjednodušší řešení může být použití funkce cílení na více verzí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k cílení na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Chcete-li vyřešit nesprávné odkazy

1. V textovém editoru otevřete soubor projektu.

2. Otevřete vlastnosti projektu.

3. Vyberte správnou **cílovou hodnotu rozhraní .NET Framework** . Alternativně můžete hodnotu prvku `<TargetFrameworkVersion>` upravit přímo v souboru projektu.

   Chcete-li, aby byl projekt spuštěn v inovované verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], je nutné aktualizovat odkazy pro projekt a také aktualizovat všechny `Imports` nebo `Using` příkazy, které volají odkazy. Pokud se váš projekt načte v integrovaném vývojovém prostředí (IDE), můžete aktualizovat odkazy pomocí **Průzkumník řešení** nebo dialogového okna **Správce odkazů** .

## <a name="see-also"></a>Viz také
 [/Upgrade (devenv. exe)](../ide/reference/upgrade-devenv-exe.md) [převod na ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
