---
title: Přizpůsobení izolovaného prostředí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555965"
---
# <a name="customizing-the-isolated-shell"></a>Přizpůsobení izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete přizpůsobit aplikaci izolovaného prostředí sady Visual Studio změnou různých aspektů uživatelského rozhraní sady Visual Studio a omezením příkazů a funkcí, které jsou součástí specializované aplikace.  
  
## <a name="using-the-applicationpkgdef-file"></a>Použití souboru Application. pkgdef  
 Řešení šablony izolovaného prostředí zahrnuje *řešení*. Soubor Application. pkgdef, který umožňuje upravit následující funkce:  
  
##### <a name="the-application-title"></a>Název aplikace  
 Můžete přizpůsobit název aplikace, což je název, který se zobrazí v záhlaví aplikace, změnou hodnoty v řádku "AppName" v názvu *řešení*. Soubor Application. pkgdef Další podrobnosti najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Pokud nechcete, aby nadpis aplikace zobrazoval projekt, který je aktuálně načten, změňte hodnotu řádku "ShowHierarchyRootInTitle" v názvu *řešení*. Soubor Application. pkgdef z DWORD: 00000001 na DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Ikona aplikace  
 Můžete přizpůsobit ikonu aplikace, což je ikona zobrazená v názvu aplikace v záhlaví aplikace. Zkopírujte jinou ikonu do adresáře ikon. V **Průzkumník řešení**přidejte ikonu do složky soubory prostředků. Pak otevřete soubor VSShellStub. RC a nahraďte hodnotu IDI_STUBPROGRAM názvem nové ikony. Další podrobnosti najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Logo příkazového řádku  
 Můžete přizpůsobit logo příkazového řádku, což je text, který se zobrazí při spuštění aplikace z příkazového řádku, a to změnou hodnoty řádku "CommandLineLogo" v poli *řešení*. Soubor Application. pkgdef Další podrobnosti najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí.](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Název podsložky uživatelských souborů  
 Můžete změnit název složky, kterou aplikace udržuje pro uživatelské soubory, a to tak, že změníte hodnotu řádku "UserFilesSubFolderName *" v názvu*souboru. Soubor Application. pkgdef  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Název uzlu stromu řešení v dialogovém okně Nový projekt  
 Název uzlu řešení v dialogovém okně Nový projekt můžete přizpůsobit tak, že změníte hodnotu řádku "NewProjDlgSlnTreeNodeTitle" v názvu *řešení*. Soubor Application. pkgdef  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Záhlaví nainstalovaných šablon v dialogovém okně Nový projekt  
 Můžete změnit hlavičku nainstalovaných šablon v dialogovém okně Nový projekt změnou hodnoty v řádku "NewProjDlgInstalledTemplatesHdr" ( *řešení*). Soubor Application. pkgdef  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Bez ohledu na to, jestli se mají ve výchozím nastavení skrývat různé soubory  
 Můžete určit, jestli se mají ve výchozím nastavení skrývat jiné soubory, a to změnou hodnoty v řádku HideMiscellaneousFilesByDefault ( *řešení*). Soubor Application. pkgdef Chcete-li skrýt různé soubory, nastavte hodnotu `dword:00000001` a chcete-li zobrazit soubory, nastavte hodnotu `dword:00000000` .  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Určuje, zda má být zakázáno okno výstup.  
 Můžete určit, zda chcete zakázat okno výstup v aplikaci změnou hodnoty řádku "DisableOutputWindow" v poli *řešení*. Soubor Application. pkgdef Chcete-li zakázat okno výstup, nastavte hodnotu `dword:00000001` a chcete-li zobrazit okno výstup, nastavte hodnotu `dword:00000000` .  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Určuje, jestli se mají v hlavním okně povoleny vyřazené soubory.  
 Můžete určit, jestli se mají v hlavním okně v aplikaci měnit soubory, a to tak, že změníte hodnotu v řádku AllowsDroppedFilesOnMainWindow ( *řešení*). Soubor Application. pkgdef Chcete-li povolit Vynechané soubory, nastavte hodnotu `dword:00000001` a zakažte Vynechané soubory, nastavte hodnotu `dword:00000000` .  
  
##### <a name="the-default-search-page"></a>Výchozí stránka pro hledání  
 Můžete přizpůsobit stránku webového prohlížeče, což je stránka, která se zobrazí, když je otevřeno okno webového prohlížeče, změnou hodnoty řádku "DefaultSearchPage" v poli *řešení*. Soubor Application. pkgdef  
  
##### <a name="the-default-home-page"></a>Výchozí domovská stránka  
 Domovskou stránku můžete přizpůsobit tak, že změníte hodnotu řádku "DefaultHomePage" v poli *řešení*. Soubor Application. pkgdef Další podrobnosti najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí.](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Bez ohledu na to, jestli se má skrýt koncept řešení  
 Můžete určit, zda chcete řešení v aplikaci skrýt, změnou hodnoty řádku "HideSolutionConcept" v poli *řešení*. Soubor Application. pkgdef Chcete-li řešení skrýt, nastavte hodnotu `dword:00000001` a k zobrazení řešení nastavte hodnotu `dword:00000000` .  
  
##### <a name="the-default-debug-engine"></a>Výchozí ladicí stroj  
 Ladicí stroj, který vaše aplikace používá, můžete změnit tak, že změníte hodnotu v řádku DefaultDebugEngine ( *řešení*). Souboru Application. pkgdef k identifikátoru GUID ladicího modulu.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Přípona souboru uživatelských možností  
 Můžete změnit název složky, kterou aplikace udržuje pro uživatelské soubory, a to tak, že změníte hodnotu řádku "UserOptsFileExt *" v názvu*souboru. Soubor Application. pkgdef  
  
##### <a name="the-solution-file-extension"></a>Přípona souboru řešení  
 Rozšíření používané pro soubory řešení můžete změnit změnou hodnoty v řádku "SolutionFileExt" ( *řešení*). Soubor Application. pkgdef  
  
##### <a name="the-default-user-files-folder-root"></a>Kořenová složka výchozích uživatelských souborů  
 Můžete změnit název kořenové složky uživatelských souborů pro aplikaci tak, že změníte hodnotu řádku "UserFilesSubFolderName" v názvu *řešení*. Soubor Application. pkgdef  
  
##### <a name="the-solution-file-creator-identifier"></a>Identifikátor autora souboru řešení  
 Identifikátor používaný pro soubory řešení můžete změnit změnou hodnoty v řádku "SolutionFileCreatorIdentifier" v poli ID *řešení*. Soubor Application. pkgdef  
  
##### <a name="the-default-projects-location"></a>Výchozí umístění projektů  
 Můžete změnit název výchozího umístění projektu změnou hodnoty řádku "DefaultProjectsLocation" v názvu *řešení*. Soubor Application. pkgdef  
  
##### <a name="the-application-localization-package"></a>Balíček lokalizace aplikace  
 Balíček lokalizace, který se používá pro vaši aplikaci, můžete změnit tak, že změníte hodnotu řádku "AppLocalizationPackage" v poli *řešení*. Soubor Application. pkgdef  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Určuje, jestli se má v názvu zobrazit kořen hierarchie.  
 Můžete určit, zda se má v záhlaví aplikace zobrazit kořen hierarchie, a to změnou hodnoty v řádku "ShowHierarchyRootInTitle" v názvu *řešení*. Soubor Application. pkgdef Chcete-li zobrazit kořen hierarchie, nastavte hodnotu `dword:00000001` a skryjte kořen hierarchie nastavením hodnoty `dword:00000000` .  
  
##### <a name="specifying-a-start-page"></a>Určení úvodní stránky  
 Chcete-li zadat úvodní stránku vlastní aplikace, v části *řešení*. Soubor Application. pkgdef, nastavte hodnotu "DisableStartPage" na `dword:00000000` a v části `[$RootKey$\StartPage\Default]` nastavit identifikátor URI na umístění souboru. XAML:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 V souboru ApplicationCommands. vsct v projektu uživatelského rozhraní pro *řešení*přidejte komentář k položce "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Musíte přidat soubor. XAML a všechny grafické soubory, které potřebujete, do projektu *řešení* . Tyto soubory musí být ve skutečnosti zkopírovány do adresáře projektu *řešení* , nepřidány z jiného adresáře.  
  
 Na všech souborech nastavte vlastnost **typ položky** na **izolovaný soubor Shell** , aby se soubory zkopírovaly do složky *$RootFolder $* . (Chcete-li nastavit vlastnost **typ položky** , klikněte pravým tlačítkem na soubor a vyberte možnost **vlastnosti**. Tato vlastnost se nachází v části **Vlastnosti konfigurace**, **Obecné**.)  
  
 Další informace o přizpůsobení spouštěcích stránek najdete v tématu [přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Používání dalších prvků izolovaného prostředí  
 K dalšímu přizpůsobení aplikace můžete použít jiné soubory a projekty, které jsou součástí šablony řešení pro izolované prostředí.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Povolit nebo zakázat balíčky sady Visual Studio  
 Soubor *řešení*. pkgundef umožňuje zakázat určité typy funkcí sady Visual Studio vyloučením určitých balíčků. Například následující řádek:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Odebere projekt různých souborů ze sady šablon projektu zobrazených v dialogovém okně **Nový projekt** . Další podrobnosti najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Povolit nebo zakázat příkazy nabídky  
 Soubor *UI.* vsct obsahuje seznam komentovaných příkazů všech příkazů nabídky dostupných pro izolované prostředí. Chcete-li zakázat daný příkaz, odkomentujte odpovídající řádek. Chcete-li například zakázat okno/rozdělit komentář, odkomentujte `<Define name="No_SplitCommand"/>` řádek. Další podrobnosti najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Rastrový obrázek použitý na úvodní obrazovce  
 Můžete přizpůsobit rastrový obrázek použitý na úvodní obrazovce, což je okno, které se zobrazí při spuštění aplikace změnou hodnoty řádku "SplashScreenBitmap" v poli *řešení*. Soubor Application. pkgdef Další podrobnosti najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Okno help/o  
 V šabloně izolovaného prostředí je k dispozici samostatný projekt, který můžete použít k přizpůsobení pole pro nápovědu/informace pro vaši aplikaci. Další podrobnosti najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
