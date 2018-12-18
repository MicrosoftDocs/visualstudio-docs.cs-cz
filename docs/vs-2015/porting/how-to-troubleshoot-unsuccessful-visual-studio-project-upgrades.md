---
title: 'Postupy: řešení potíží s upgrady neúspěšný projekt | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 6b50bbaaf7e5b018709f3cf0dece3c0ae38410f8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064790"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Postupy: Řešení potíží spojených s neúspěšným upgradem projektu sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Někdy Visual Studio nemůže převést plně projektu ze starší verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pokud se určitý problém nelze vyřešit pomocí tipů v následujících částech, bude pravděpodobně možné na další informace naleznete na následující článek knihovny TechNet [Wiki: portál vývoj](http://go.microsoft.com/fwlink/?LinkId=254808).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Projekt se nespustí, protože nebyly nalezeny soubory
 Soubor projektu obsahuje soubor pevně zakódované cesty, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] používá ke spuštění projektu při stisknutí klávesy F5. Tyto cesty mohou být umístění devenv.exe a další požadované soubory. V upgradované verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cesty tyto soubory byly změněny.

#### <a name="to-resolve-incorrect-file-paths"></a>Chcete-li vyřešit nesprávné cesty k souborům

1.  V textovém editoru otevřete soubor projektu.

2.  Vyhledání cesty k souborům, které může být nesprávný, zejména těch, které obsahují [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] číslo verze.

3.  Úprava cesty k souboru tak, aby ukazovaly na novou cíle.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Projekt sestavit, protože odkazy nejsou platné
 Při upgradu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], může také být upgradu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verze. Pokud váš projekt obsahuje odkazy, které jsou zrušeny ve verzi novější [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verze, se nemůže vyřešit správně. To je zvláště pravděpodobné odkazy, které zahrnují číslo verze, například `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Pokud váš kód obsahuje mnoho neplatné odkazy, nejjednodušším řešením může být pomocí funkce cílení na více platforem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cílit na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Chcete-li vyřešit nesprávné odkazy

1. V textovém editoru otevřete soubor projektu.

2. Otevřete vlastnosti projektu.

3. Vyberte správné **Cílová architektura** hodnotu. Alternativně můžete změnit hodnotu `<TargetFrameworkVersion>` element přímo v souboru projektu.

   Pokud chcete, aby projektu pro spuštění v upgradovaný [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verze, musíte aktualizovat odkazy na projekt a aktualizujte také některé `Imports` nebo `Using` příkazy, které volají odkazy. Pokud váš projekt je načten v integrovaném vývojovém prostředí, můžete aktualizovat odkazy pomocí **Průzkumníka řešení** nebo **správce odkazů** dialogové okno.

## <a name="see-also"></a>Viz také
 [/ Upgrade (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [převod na technologii ASP.NET 4](http://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
