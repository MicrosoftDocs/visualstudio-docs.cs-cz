---
title: Nasazení VSIX DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916551"
---
# <a name="vsix-deployment-of-a-dsl"></a>Nasazení na VSIX DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jazyk specifický pro doménu můžete nainstalovat na vlastní počítač nebo na jiné počítače. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v cílovém počítači již musí být nainstalována.

## <a name="installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Instalace a odinstalace DSL pomocí VSX
 Pokud je vaše DSL nainstalovaná touto metodou, uživatel může otevřít soubor DSL v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ale soubor nejde otevřít v Průzkumníkovi Windows.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>Instalace DSL pomocí VSIX

1. V počítači vyhledejte soubor **. vsix** , který byl vytvořen projektem balíčku DSL.

    1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **DslPackage** a potom klikněte na možnost **Otevřít složku v Průzkumníku Windows**.

    2. Vyhledejte soubor ** \\ \* \\ bin**_YourProject_**. DslPackage. vsix**

2. Zkopírujte soubor **. vsix** do cílového počítače, do kterého chcete nainstalovat DSL. Může to být váš vlastní počítač nebo jiný.

    - Cílový počítač musí mít jednu z edicí [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , která podporuje DSL v době běhu. Další informace najdete v tématu [podporované edice sady Visual Studio pro vizualizaci & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Cílový počítač musí mít jednu z edicí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] specifikovanou v **DslPackage\source.Extensions.manifest**.

3. V cílovém počítači poklikejte na soubor **. vsix** .

     **Instalační program rozšíření sady Visual Studio** se otevře a nainstaluje rozšíření.

4. Spusťte nebo restartujte [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

5. K otestování DSL použijte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k vytvoření nového souboru s příponou, kterou jste definovali pro DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Postup při odinstalaci DSL nainstalované pomocí VSX

1. V nabídce **nástroje** klikněte na **Správce rozšíření**.

2. Rozbalte položku **nainstalovaná rozšíření**.

3. Vyberte rozšíření, ve kterém je definována DSL, a pak klikněte na **odinstalovat**.

   Zřídka se vadné rozšíření nedokáže načíst a vytvoří sestavu v okně chyb, ale nezobrazí se ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z:

   *Localappdata* **\Microsoft\VisualStudio\10.0\Extensions**
