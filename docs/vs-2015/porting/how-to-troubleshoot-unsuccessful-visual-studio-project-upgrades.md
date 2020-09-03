---
title: 'Postupy: řešení neúspěšných upgradů projektů | Microsoft Docs'
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
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844440"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Postupy: Řešení potíží spojených s neúspěšným upgradem projektu sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Může se stát, že Visual Studio nemůže plně převést projekt ze starší verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pokud tipy v následujících částech nevyřeší váš konkrétní problém, může být možné najít další informace na [wikiwebu TechNet: vývojový portál](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Projekt se nespustí, protože se nenašly soubory.
 Soubor projektu obsahuje pevně zakódované cesty k souborům, které [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroj používá ke spuštění projektu při stisknutí klávesy F5. Tyto cesty mohou zahrnovat umístění devenv.exe a další požadované soubory. V upgradovaných verzích nástroje byly [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pravděpodobně změněny cesty těchto souborů.

#### <a name="to-resolve-incorrect-file-paths"></a>Vyřešení neplatných cest k souborům

1. Otevřete soubor projektu v textovém editoru.

2. Vyhledat cesty k souborům, které mohou být nesprávné, zejména ty, které obsahují [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] číslo verze.

3. Upravte nesprávné cesty k souboru tak, aby odkazovaly na nové cíle.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Projekt se nevytváří, protože odkazy nejsou platné.
 Při upgradu nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] můžete také upgradovat [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi. Pokud váš projekt obsahuje odkazy, které byly v novější verzi ukončeny [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , nemusí se vyřešit správně. To je obzvláště nejspíš u odkazů, které obsahují čísla verzí, například `Microsoft.VisualStudio.Shell.Interop.8.0` .

 Pokud má váš kód mnoho neplatných odkazů, nejjednodušší řešení může být použití funkce cílení na více verzí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro cílení na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

#### <a name="to-resolve-incorrect-references"></a>Vyřešení neplatných odkazů

1. Otevřete soubor projektu v textovém editoru.

2. Otevřete vlastnosti projektu.

3. Vyberte správnou **cílovou hodnotu rozhraní .NET Framework** . Alternativně můžete hodnotu `<TargetFrameworkVersion>` prvku upravit přímo v souboru projektu.

   Chcete-li, aby projekt běžel v inovované [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi, je nutné aktualizovat odkazy na projekt a také aktualizovat jakékoli `Imports` `Using` příkazy nebo, které volají odkazy. Pokud se váš projekt načte v integrovaném vývojovém prostředí (IDE), můžete aktualizovat odkazy pomocí **Průzkumník řešení** nebo dialogového okna **Správce odkazů** .

## <a name="see-also"></a>Viz také
 [/Upgrade (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [převod na ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
