---
title: Rozšíření izolovaného prostředí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799312"
---
# <a name="extending-the-isolated-shell"></a>Rozšíření izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Izolované prostředí sady Visual Studio můžete roztáhnout přidáním součásti VSPackage, komponenty Managed Extensibility Framework (MEF) nebo obecného projektu VSIX do aplikace izolovaného prostředí.  
  
> [!NOTE]
> Následující kroky presuppose, že jste vytvořili základní aplikaci izolovaného prostředí pomocí šablony projektu izolované prostředí sady Visual Studio. Další informace o této šabloně projektu naleznete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Umístění pro šablonu projektu balíčku sady Visual Studio  
 Šablona projektu balíčku sady Visual Studio se dá najít ve třech různých umístěních v dialogovém okně **Nový projekt** :  
  
1. V **Visual Basic**části Visual Basic **rozšiřitelnost**. Výchozí jazyk projektu je Visual Basic.  
  
2. V části **Visual C#** **rozšiřitelnost**. Výchozím jazykem projektu je C#.  
  
3. V části **ostatní typy projektů** **rozšiřitelnost**. Výchozí jazyk projektu je C++.  
  
## <a name="adding-a-vspackage"></a>Přidání balíčku VSPackage  
 Do aplikace izolovaného prostředí můžete přidat VSPackage. Následující kroky ukazují, jak vytvořit jeden, který přidá příkazy nabídky.  
  
#### <a name="to-add-a-new-vspackage"></a>Přidání nového balíčku VSPackage  
  
1. Přidejte projekt balíčku sady Visual Studio s názvem `MenuCommandsPackage` .  
  
2. Na stránce **základní informace** o rozhraní VSPackage průvodce nastavte **název společnosti** na `Fabrikam` a **název VSPackage** na `FabrikamMenuCommands` . Klikněte na tlačítko **Další** .  
  
3. Na další stránce vyberte **příkaz nabídky** a klikněte na tlačítko **Další**.  
  
4. Na další stránce nastavte **název příkazu** na `Fabrikam Command` a **ID příkazu** na a pak klikněte na `cmdidFabrikamCommand` tlačítko **Další**.  
  
5. Na stránce **Vybrat možnosti projektu testu** zrušte zaškrtnutí možnosti testu a pak klikněte na tlačítko **Dokončit** .  
  
6. V projektu ShellExtensionsVSIX otevřete soubor source. extension. vsixmanifest.  
  
     Oddíl **assets** by měl obsahovat položku pro projekt VSShellStub. AboutBoxPackage.  
  
7. Klikněte na tlačítko **Nový** .  
  
8. V okně **Přidat nový prostředek** vyberte v seznamu **typ** možnost **Microsoft. VisualStudio. VSPackage**.  
  
9. V seznamu **zdroj** se ujistěte, že je vybrán **projekt v aktuálním řešení** . V poli seznam **projektu** vyberte možnost **MenuCommandsPackage**.  
  
10. Uložte soubor a zavřete ho.  
  
11. Znovu sestavte řešení a spusťte ladění izolovaného prostředí.  
  
12. Na řádku nabídek klikněte na nabídku **nástroje** a pak na **příkaz Fabrikam**.  
  
     Mělo by se zobrazit okno se zprávou.  
  
13. Zastavit ladění aplikace  
  
## <a name="adding-a-mef-component-part"></a>Přidání části součásti MEF  
 Následující kroky ukazují, jak přidat součást MEF do aplikace izolovaného prostředí.  
  
#### <a name="to-add-a-mef-component"></a>Přidání komponenty MEF  
  
1. V dialogovém okně **Přidat nový projekt** v části **Visual C#** **rozšiřitelnost**použijte šablonu **okraje editoru** k přidání projektu. Pojmenujte ji `ShellEditorMargin`.  
  
2. V projektu ShellExtensionsVSIX otevřete soubor source. extension. vsixmanifest v zobrazení Návrh, nikoli v zobrazení kódu.  
  
3. V `Asset` části vyberte možnost **Přidat obsah**.  
  
4. V okně **Přidat nový prostředek** vyberte v seznamu **typ** možnost **Microsoft. VisualStudio. MefComponent**.  
  
5. V seznamu **zdroj** se ujistěte, že je vybrán **projekt v aktuálním řešení** . V poli seznam **projektu** vyberte možnost **ShellEditorMargin**.  
  
6. Uložte soubor a zavřete ho.  
  
7. Znovu sestavte řešení a spusťte ladění izolovaného prostředí.  
  
8. Otevřete textový soubor.  
  
     Zelený okraj, který obsahuje slova "Hello World!" by se mělo zobrazit v dolní části okna textový soubor.  
  
9. Zastavit ladění aplikace  
  
## <a name="adding-a-generic-vsix-project"></a>Přidání obecného projektu VSIX  
  
#### <a name="to-add-a-generic-vsix-project"></a>Přidání obecného projektu VSIX  
  
1. V dialogovém okně **Přidat nový projekt** v části **Visual C#** **rozšiřitelnost**použijte šablonu **VSIXProject** pro přidání projektu. Pojmenujte ji `EmptyVSIX`.  
  
2. V projektu ShellExtensionsVSIX otevřete soubor source. Extensions. vsixmanifest v zobrazení Návrh, nikoli v zobrazení kódu.  
  
3. V `Assets` části vyberte možnost **Nový**.  
  
4. V okně **Přidat nový prostředek** v seznamu **typ** vyberte typ obsahu, který chcete přidat.  
  
5. V části **zdroj**se ujistěte, že je vybrána možnost **projekt v aktuální řešení** . V poli seznam vyberte název projektu VSIX.  
  
6. Uložte soubor a zavřete ho.  
  
7. Pokud tento projekt obsahuje zkompilovaný kód, je nutné upravit projekt tak, aby bylo sestavení zahrnuto do výstupu.  
  
    1. Uvolněte projekt VSIX a otevřete soubor projektu.  
  
    2. V prvním `<PropertyGroup>` bloku změňte hodnotu `<CopyBuildOutputToOutputDirectory>` na `true` .  
  
    3. Uložte a znovu načtěte projekt.  
  
8. Sestavte a spusťte řešení.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
