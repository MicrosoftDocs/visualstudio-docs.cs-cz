---
title: Možnosti a stránky Možnosti | Dokumentace Microsoftu
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
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 005aeceb328a24c8c90994b6b274dbddc6b874f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783269"
---
# <a name="options-and-options-pages"></a>Možnosti a stránky Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kliknutím na **možnosti** na **nástroje** se otevře nabídka **možnosti** dialogové okno. Možnosti v tomto dialogovém se souhrnně označují jako možnosti stránky. Ovládací prvek stromové struktury v navigačním podokně zahrnuje možnosti kategorií a každou kategorii má možnosti stránky. Když vyberete na stránce, jeho možnosti se zobrazí v pravém podokně. Tyto stránky umožňují změnit hodnoty možnosti, které určují stav VSPackage.  
  
## <a name="support-for-options-pages"></a>Podpora pro stránky Možnosti  
 <xref:Microsoft.VisualStudio.Shell.Package> Třída poskytuje podporu pro vytváření stránek možnosti a možnosti kategorií. <xref:Microsoft.VisualStudio.Shell.DialogPage> Třída implementuje stránku možností.  
  
 Výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage> nabízí jeho veřejné vlastnosti uživatele v obecné mřížky vlastností. Toto chování můžete přizpůsobit tak, že přepíšete různé metody na stránce vytvořit vlastní možnosti stránku, která má své vlastní uživatelské rozhraní (UI). Další informace najdete v tématu [vytvoření stránky možnosti](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Implementuje třída <xref:Microsoft.VisualStudio.Shell.IProfileManager>, který poskytuje trvalosti pro stránky možnosti a také pro nastavení uživatele. Výchozí implementace <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> a <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metody zachovat změny vlastností do části uživatele z registru, pokud lze vlastnost převést do a z řetězce.  
  
## <a name="options-page-registry-path"></a>Cesta v registru stránky Možnosti  
 Ve výchozím nastavení, je určen cestu registru vlastností spravuje stránky možnosti tím, že zkombinujete <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, slovo třídy DialogPage a název typu třídy stránky možnosti. Například třída stránky možností mohou být definovány následovně.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Pokud <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> je HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, pak vlastnost dvojice název a hodnotu podklíče HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Cesta registru samotná stránka možností je určen tím, že zkombinujete <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, slovo, ToolsOptionsPages a možnosti stránce kategorie a název. Například, pokud kategorie Mé stránky možnost má vlastní stránky možnosti a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> je HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, pak na stránce možnosti nemá klíč registru, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Možnost Pages\Custom VisualStudio\8.0Exp\ToolsOptionsPages\My.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Nástroje/možnosti atributy stránky a rozložení  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Určuje atribut seskupení vlastních stránek možností do kategorií v navigačním stromu **možnosti** dialogové okno. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Atribut přidruží sady VSPackage, která poskytuje rozhraní pro stránky možnosti. Předpokládejme následující fragment kódu:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 To deklaruje, že MyPackage obsahuje dvě stránky možnosti OptionsPageGeneral a OptionsPageCustom. V **možnosti** dialogové okno, obě možnosti stránky se zobrazují v **vlastní stránky možnosti** kategorie jako **Obecné** a **vlastní**v uvedeném pořadí.  
  
## <a name="option-attributes-and-layout"></a>Možnost atributy a rozložení  
 Uživatelské rozhraní (UI), které na stránce určuje vzhled možnosti na stránce vlastní možnosti. Rozložení, označování popisky a popis možnosti na stránce Obecné možnosti jsou určeny následující atributy:  
  
- <xref:System.ComponentModel.CategoryAttribute> Určuje kategorii možnost.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> Určuje zobrazovaný název možnosti.  
  
- <xref:System.ComponentModel.DescriptionAttribute> Určuje popis možnosti.  
  
  > [!NOTE]
  >  Ekvivalentní atributy, SRCategory, LocDisplayName a SRDescription, použití řetězcových prostředků pro lokalizaci a jsou definovány v [spravovaný projekt ukázky](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Předpokládejme následující fragment kódu:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  Možnost OptionInteger se zobrazí na stránce možnosti jako **celé číslo možnost** v **Moje možnosti** kategorie. Pokud je vybraná možnost, popis, **možnost Moje celé číslo**, zobrazí se v poli Popis.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Přístup k možnosti stránky z jiného balíčku VSPackage  
 VSPackage, která hostuje a spravuje stránky možnosti můžete programově přistupovat z jiného balíčku VSPackage pomocí modelu automatizace. Například v následujícím kódu se VSPackage zaregistruje jako hostování stránce možností.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Následující fragment kódu získá hodnotu OptionInteger z MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Když <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atribut zaregistruje stránky možnosti, na stránce je zaregistrovaný pod if klíče AutomationProperties `SupportsAutomation` argument atributu je `true`. Automatizace prozkoumá této položky registru najít související balíček VSPackage správy kódu a automatizaci pak přistupuje k vlastnosti prostřednictvím hostované možnosti stránky, v tomto případě stránku mřížky.  
  
 Vlastnosti automatizace cestu registru je určen tím, že zkombinujete <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, slovo, vlastnosti automatizace a možnosti stránce kategorie a název. Například, pokud na stránce Možnosti má kategorii mé kategorie, název mé stránky mřížky a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp a pak vlastnost automatizace má klíč registru, HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My mřížky stránky.  
  
> [!NOTE]
>  Kanonický název mé stránky mřížky Category.My, je hodnota podklíče název tohoto klíče.

