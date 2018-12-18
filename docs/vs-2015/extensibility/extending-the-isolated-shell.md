---
title: Rozšíření izolovaného prostředí | Dokumentace Microsoftu
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
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc700e0a1b8753a26067eff90df9ff58765de8d1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792018"
---
# <a name="extending-the-isolated-shell"></a>Rozšíření izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prostředí sady Visual Studio, samostatný můžete rozšířit přidáním VSPackage, součást Managed Extensibility Framework (MEF) nebo projektu s obecným VSIX do vaší aplikace izolovaného prostředí.  
  
> [!NOTE]
>  Následující kroky předpokládají, že jste vytvořili základní aplikace izolovaného prostředí pomocí Visual Studio Shell izolované šablony projektu. Další informace o této šabloně projektu naleznete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Umístění pro šablony sady Visual Studio balíčku projektu  
 Šablona projektu balíček Visual Studio najdete ve třech různých umístěních v **nový projekt** dialogové okno:  
  
1.  V části **jazyka Visual Basic**, **rozšiřitelnost**. Je výchozí jazyk projektu jazyka Visual Basic.  
  
2.  V části **Visual C#**, **rozšiřitelnost**. Je výchozí jazyk projektu C#.  
  
3.  V části **ostatní typy projektů**, **rozšiřitelnost**. Výchozí jazyk projektu je C++.  
  
## <a name="adding-a-vspackage"></a>Přidání VSPackage  
 VSPackage můžete přidat do vaší aplikace izolovaného prostředí. Následující kroky ukazují, jak vytvořit takový, který přidá příkazy nabídky.  
  
#### <a name="to-add-a-new-vspackage"></a>Chcete-li přidat nový VSPackage  
  
1.  Přidat projekt balíčku Visual Studio s názvem `MenuCommandsPackage`.  
  
2.  Na **základní informace o sadě VSPackage** stránku průvodce, nastavte **název společnosti** k `Fabrikam` a **název balíčku VSPackage** k `FabrikamMenuCommands`. Zvolte **Další** tlačítko.  
  
3.  Na další stránce vyberte **příkazu nabídky** a klikněte na tlačítko **Další**.  
  
4.  Na další stránku, nastavte **název příkazu** k `Fabrikam Command` a **ID příkazu** k `cmdidFabrikamCommand`a klikněte na tlačítko **Další**.  
  
5.  Na **vyberte možnosti projektu testování** stránce, zrušte zaškrtnutí možnosti testování a klikněte na tlačítko **Dokončit** tlačítko.  
  
6.  V projektu ShellExtensionsVSIX otevřete soubor source.extension.vsixmanifest.  
  
     **Prostředky** oddíl by měl obsahovat položku VSShellStub.AboutBoxPackage projektu.  
  
7.  Zvolte **nový** tlačítko.  
  
8.  V **přidat nové aktivum** okno v **typ** seznamu vyberte **Microsoft.VisualStudio.VsPackage**.  
  
9. V **zdroj** seznamu, ujistěte se, že **projekt v aktuálním řešení** zaškrtnuto. V **projektu** pole se seznamem, vyberte **MenuCommandsPackage**.  
  
10. Soubor uložte a zavřete.  
  
11. Znovu sestavte řešení a spustit ladění izolovaného prostředí.  
  
12. V panelu nabídky zvolte **nástroje** nabídce a potom **Fabrikam příkaz**.  
  
     By se zobrazit okno se zprávou.  
  
13. Zastavte ladění aplikace.  
  
## <a name="adding-a-mef-component-part"></a>Přidání součásti MEF  
 Následující kroky ukazují, jak do vaší aplikace izolovaného prostředí přidat součást MEF.  
  
#### <a name="to-add-a-mef-component"></a>K přidání komponenty MEF  
  
1.  V **přidat nový projekt** dialogovém okně **Visual C#**, **rozšiřitelnost**, použijte **okraj editoru** šablonu pro přidání do projektu. Pojmenujte ji `ShellEditorMargin`.  
  
2.  V projektu ShellExtensionsVSIX otevřete soubor Source.extension.vsixmanifest v zobrazení návrhu zobrazení kódu.  
  
3.  V `Asset` zvolte **přidat obsah**.  
  
4.  V **přidat nové aktivum** okno v **typ** seznamu vyberte **Microsoft.VisualStudio.MefComponent**.  
  
5.  V **zdroj** seznamu, ujistěte se, že **projekt v aktuálním řešení** zaškrtnuto. V **projektu** pole se seznamem, vyberte **ShellEditorMargin**.  
  
6.  Soubor uložte a zavřete.  
  
7.  Znovu sestavte řešení a spustit ladění izolovaného prostředí.  
  
8.  Otevřete textový soubor.  
  
     Zelená okraj obsahující slova "Hello world!" má být zobrazena v dolní části okna textového souboru.  
  
9. Zastavte ladění aplikace.  
  
## <a name="adding-a-generic-vsix-project"></a>Přidání projektu VSIX obecné  
  
#### <a name="to-add-a-generic-vsix-project"></a>Přidání obecného projektu VSIX  
  
1.  V **přidat nový projekt** dialogovém okně **Visual C#**, **rozšiřitelnost**, použijte **VSIXProject** šablonu pro přidání do projektu. Pojmenujte ji `EmptyVSIX`.  
  
2.  V projektu ShellExtensionsVSIX otevřete soubor Source.extensions.vsixmanifest v zobrazení návrhu zobrazení kódu.  
  
3.  V `Assets` zvolte **nový**.  
  
4.  V **přidat nové aktivum** okno v **typ** vyberte typ obsahu, které chcete přidat.  
  
5.  V **zdroj**, ujistěte se, že **projekt v aktuálním řešení** je vybraná možnost. V rozevíracím seznamu vyberte název vaším projektem VSIX.  
  
6.  Soubor uložte a zavřete.  
  
7.  Pokud tento projekt obsahuje zkompilovaný kód, je nutné upravit projektu tak, aby sestavení je zahrnout do výstupu.  
  
    1.  Uvolněte projekt VSIX a otevřete soubor projektu.  
  
    2.  V prvním `<PropertyGroup>` blokovat, změňte hodnotu vlastnosti `<CopyBuildOutputToOutputDirectory>` k `true`.  
  
    3.  Uložit a znovu načíst projekt.  
  
8.  Sestavte a spusťte řešení.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

