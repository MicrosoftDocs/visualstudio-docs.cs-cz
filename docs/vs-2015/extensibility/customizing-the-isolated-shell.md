---
title: Přizpůsobení izolovaného prostředí | Dokumentace Microsoftu
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
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097186ba43202c537bf8acbe0b47893151055c19
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733776"
---
# <a name="customizing-the-isolated-shell"></a>Přizpůsobení izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace Visual Studio izolované prostředí můžete přizpůsobit tak, že změníte různé aspekty uživatelského rozhraní sady Visual Studio a omezení příkazů a funkcí obsažených v aplikaci speciální.  
  
## <a name="using-the-applicationpkgdef-file"></a>Použití souboru Application.pkgdef  
 Šablona řešení izolovaného prostředí zahrnuje *SolutionName*. Application.pkgdef soubor, který umožňuje změnit následující funkce:  
  
##### <a name="the-application-title"></a>Název aplikace  
 Můžete přizpůsobit název aplikace, což je název, který se zobrazí v záhlaví okna aplikace, můžete změnit hodnotu na řádek "AppName" *SolutionName*. Application.pkgdef souboru. Další podrobnosti najdete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Pokud nechcete, aby název aplikace, chcete-li zobrazit projekt, který je aktuálně načtená, změňte hodnotu na řádek "ShowHierarchyRootInTitle" *SolutionName*. Application.pkgdef souboru z DWORD: 00000001 DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Ikona aplikace  
 Můžete přizpůsobit ikonu aplikace, což je ikona, která se zobrazí podle názvu aplikace v záhlaví okna aplikace. K adresáři ikonu zkopírujte jinou ikonu. V **Průzkumníka řešení**, přidejte ikonu složky souborů prostředků. Pak otevřete soubor VSShellStub.rc a nahraďte hodnotu IDI_STUBPROGRAM s názvem na ikonu nový. Další podrobnosti najdete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Logo příkazového řádku  
 Můžete přizpůsobit logo příkazového řádku, což je text, který se zobrazí při spuštění aplikace z příkazového řádku, můžete změnit hodnotu na řádek "CommandLineLogo" *SolutionName*. Application.pkgdef souboru. Další podrobnosti najdete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Název podsložky soubory uživatele  
 Můžete změnit název složky, které vaše aplikace udržuje pro soubory uživatele tak, že změníte hodnotu "UserFilesSubFolderName" řádku v *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Název uzlu stromové struktury řešení v dialogovém okně Nový projekt  
 Název uzlu řešení v dialogovém okně Nový projekt můžete přizpůsobit tak, že změníte hodnotu "NewProjDlgSlnTreeNodeTitle" řádku v *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Hlavička nainstalovaných šablon v dialogovém okně Nový projekt  
 Hlavička nainstalovaných šablon v dialogovém okně Nový projekt můžete změnit tak, že změníte hodnotu "NewProjDlgInstalledTemplatesHdr" řádku v *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Jestli se mají skrýt různé soubory ve výchozím nastavení  
 Můžete určit, jestli se mají skrýt různé soubory ve výchozím nastavení můžete změnit hodnotu na řádek "HideMiscellaneousFilesByDefault" *SolutionName*. Application.pkgdef souboru. Chcete-li skrýt různé soubory, nastavte hodnotu `dword:00000001`a pokud chcete zobrazit soubory, nastavte hodnotu `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Jestli chcete zakázat v okně Výstup  
 Můžete určit, jestli se má zakázat okno výstup v aplikaci tak, že změníte hodnotu "DisableOutputWindow" řádku v *SolutionName*. Application.pkgdef souboru. Chcete-li zakázat v okně výstupu, nastavte hodnotu `dword:00000001`a chcete-li zobrazit okno výstupu, nastavte hodnotu `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Jestli chcete povolit přetažené soubory hlavního okna  
 Můžete určit, jestli se mají povolit přetažené soubory v hlavním okně aplikace můžete změnit hodnotu na řádek "AllowsDroppedFilesOnMainWindow" *SolutionName*. Application.pkgdef souboru. Chcete-li povolit přetažené soubory, nastavte hodnotu `dword:00000001`a pokud chcete zakázat přetažené soubory, nastavte hodnotu `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Výchozí stránku vyhledávání  
 Stránka webového prohlížeče, což je stránka, která se zobrazí při otevření okna webového prohlížeče, můžete změnit hodnotu na řádek "DefaultSearchPage" můžete přizpůsobit *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="the-default-home-page"></a>Výchozí domovskou stránku  
 Na domovskou stránku můžete přizpůsobit tak, že změníte hodnotu "DefaultHomePage" řádku v *SolutionName*. Application.pkgdef souboru. Další podrobnosti najdete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Jestli se mají skrýt koncept řešení  
 Můžete určit, jestli se mají skrýt řešení ve vaší aplikaci můžete změnit hodnotu na řádek "HideSolutionConcept" *SolutionName*. Application.pkgdef souboru. Chcete-li skrýt toto řešení, nastavte hodnotu `dword:00000001`a pokud chcete zobrazit řešení, nastavte hodnotu `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Výchozí ladicího stroje  
 Můžete změnit ladicí stroj vaše aplikace používá tak, že změníte hodnotu na řádek "DefaultDebugEngine" *SolutionName*. Soubor Application.pkgdef na identifikátor GUID ladicího stroje.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Přípona souboru s možností uživatele  
 Můžete změnit název složky, které vaše aplikace udržuje pro soubory uživatele tak, že změníte hodnotu "UserOptsFileExt" řádku v *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="the-solution-file-extension"></a>Přípona souboru řešení  
 Rozšíření pro soubory řešení můžete změnit hodnotu na řádek "SolutionFileExt" můžete změnit *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="the-default-user-files-folder-root"></a>Výchozí uživatelské soubory složky kořen  
 Můžete změnit název kořenové složky souborů uživatele pro vaši aplikaci můžete změnit hodnotu na řádek "UserFilesSubFolderName" *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="the-solution-file-creator-identifier"></a>Identifikátor Tvůrce soubor řešení  
 Můžete změnit identifikátor použitý pro soubory řešení můžete změnit hodnotu na řádek "SolutionFileCreatorIdentifier" *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="the-default-projects-location"></a>Výchozí umístění projektů  
 Název výchozí umístění projektů můžete změnit tak, že změníte hodnotu "DefaultProjectsLocation" řádku v *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="the-application-localization-package"></a>Lokalizační balíček aplikace  
 Můžete měnit balíček lokalizace, používá pro vaši aplikaci tak, že změníte hodnotu "AppLocalizationPackage" řádku v *SolutionName*. Application.pkgdef souboru.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Jestli se mají zobrazit kořenu hierarchie v názvu  
 Můžete určit, jestli se mají zobrazit tak, že změníte hodnotu "ShowHierarchyRootInTitle" řádku v kořenu hierarchie v záhlaví okna ve vaší aplikaci *SolutionName*. Application.pkgdef souboru. Chcete-li zobrazit kořenu hierarchie, nastavte hodnotu `dword:00000001`a pokud chcete skrýt kořen hierarchie, nastavte hodnotu `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Určení úvodní stránky  
 Chcete-li určit úvodní stránky pro vaše vlastní aplikace v *SolutionName*. Soubor Application.pkgdef, nastavte na hodnotu "DisableStartPage" `dword:00000000`a v části `[$RootKey$\StartPage\Default]` nastavení identifikátoru URI k umístění souboru .xaml:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 V souboru Applicationcommands.vsct *SolutionName*projektu uživatelského rozhraní, Odkomentujte položku "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Je nutné přidat soubor .xaml a všechny soubory grafiky, potřebujete na *SolutionName* projektu. Tyto soubory musí být ve skutečnosti zkopírují do *SolutionName* adresáře projektu, nebyla přidána z některé adresáře.  
  
 Na všechny soubory, nastavte **typ položky** vlastnost **izolovaného prostředí soubor** v pořadí pro soubory, které se mají zkopírovat do *$RootFolder$* adresáře. (Chcete-li nastavit **typ položky** vlastnosti, klikněte pravým tlačítkem na soubor a vyberte **vlastnosti**. Tato vlastnost se nachází v **vlastnosti konfigurace**, **Obecné**.)  
  
 Další informace o přizpůsobení úvodní stránky najdete v tématu [přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Pomocí další prvky izolovaného prostředí  
 Můžete použít další soubory a projekty, které jsou součástí šablony řešení izolovaného prostředí můžete dále přizpůsobit aplikaci.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Povolí nebo zakáže balíčky Visual Studio  
 *SolutionName*souboru .pkgundef umožňuje vyloučení určitých balíčků vypnout určité druhy funkce sady Visual Studio. Například následující řádek:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Odebere ze sady šablon projektů, které jsou zobrazeny v ostatních souborech projektu **nový projekt** dialogového okna. Další podrobnosti najdete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Povolit nebo zakázat příkazy nabídky  
 *SolutionName*UI.vsct soubor obsahuje seznam všech příkazů nabídky k dispozici pro izolovaného prostředí komentovaná. Chcete-li zakázat zadaný příkaz, Odkomentujte odpovídající řádek. Například pokud chcete zakázat komentáře/rozdělení okna, zrušte komentář `<Define name="No_SplitCommand"/>` řádek. Další podrobnosti najdete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Rastrový obrázek používá na úvodní obrazovce  
 Můžete přizpůsobit rastrový obrázek používá na úvodní obrazovce, která je okno, které se zobrazí, když je aplikace spuštěna, můžete změnit hodnotu na řádek "SplashScreenBitmap" *SolutionName*. Application.pkgdef souboru. Další podrobnosti najdete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Nápověda/o okně  
 V šabloně izolovaného prostředí je samostatný projekt, můžete použít k přizpůsobení Nápověda/o pole pro vaši aplikaci. Další podrobnosti najdete v tématu [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).

