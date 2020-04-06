---
title: Stránky možností a možností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706837"
---
# <a name="options-and-options-pages"></a>Možnosti a stránky Možnosti
Klepnutím na **možnosti** v nabídce **Nástroje** se otevře dialogové okno **Možnosti.** Možnosti v tomto dialogovém okně jsou souhrnně označovány jako stránky možností. Ovládací prvek stromu v navigačním podokně obsahuje kategorie možností a každá kategorie má stránky možností. Když vyberete stránku, její možnosti se zobrazí v pravém podokně. Tyto stránky umožňují změnit hodnoty možností, které určují stav VSPackage.

## <a name="support-for-options-pages"></a>Podpora stránek možností
 Třída <xref:Microsoft.VisualStudio.Shell.Package> poskytuje podporu pro vytváření stránek možností a kategorií možností. Třída <xref:Microsoft.VisualStudio.Shell.DialogPage> implementuje stránku možností.

 Výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage> nabízí své veřejné vlastnosti uživateli v obecné mřížce vlastností. Toto chování můžete přizpůsobit přepsáním různých metod na stránce a vytvořit vlastní stránku možností, která má vlastní uživatelské rozhraní. Další informace naleznete [v tématu Vytvoření stránky možností](../../extensibility/creating-an-options-page.md).

 Třída <xref:Microsoft.VisualStudio.Shell.DialogPage> implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager>, který poskytuje trvalost pro stránky možností a také pro nastavení uživatele. Výchozí implementace <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> a <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metody zachovat změny vlastností do uživatelské části registru, pokud vlastnost lze převést do a z řetězce.

## <a name="options-page-registry-path"></a>Cesta registru stránky Možnosti
 Ve výchozím nastavení je cesta registru vlastností spravovaných <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>stránkou možností určena kombinací , slovem DialogPage a názvem typu třídy stránky options. Třída stránky možností může být například definována následujícím způsobem.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Pokud <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> je HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, pak jsou dvojice názvů vlastností a hodnot podklíčiHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Cesta registru samotné stránky možností je určena <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>kombinací , slovo, ToolsOptionsPages a možnosti stránky kategorie a název. Pokud má například stránka Vlastní možnosti kategorii Moje option <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> pages a je HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, pak stránka možností obsahuje klíč registru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Atributy a rozložení stránky Nástroje/možnosti
 Atribut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> určuje seskupení stránek vlastních možností do kategorií v navigačním stromu dialogového okna **Možnosti.** Atribut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> přidruží stránku možností k balíčku VSPackage, který poskytuje rozhraní. Předpokládejme následující fragment kódu:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 To deklaruje, že MyPackage poskytuje dvě stránky možností, OptionsPageGeneral a OptionsPageCustom. V dialogovém okně **Možnosti** se obě stránky možností zobrazí v kategorii **Moje stránky možností** jako **Obecné** a **Vlastní**.

## <a name="option-attributes-and-layout"></a>Atributy a rozložení možností
 Uživatelské rozhraní (UI), které stránka poskytuje, určuje vzhled možností na stránce vlastních možností. Rozložení, popisky a popis možností na stránce obecných možností jsou určeny následujícími atributy:

- <xref:System.ComponentModel.CategoryAttribute>určuje kategorii možnosti.

- <xref:System.ComponentModel.DisplayNameAttribute>určuje zobrazovaný název možnosti.

- <xref:System.ComponentModel.DescriptionAttribute>určuje popis možnosti.

  > [!NOTE]
  > Ekvivalentní atributy, SRCategory, LocDisplayName a SRDescription, používají prostředky řetězce pro lokalizaci a jsou definovány ve [vzorku spravovaného projektu](/azure/devops/integrate/index).

  Předpokládejme následující fragment kódu:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Možnost OptionInteger se zobrazí na stránce možností jako **Možnost celého čísla** v kategorii **Moje možnosti.** Pokud je tato možnost vybraná, zobrazí se v poli popisu popis, **možnost Celé číslo**.

## <a name="accessing-options-pages-from-another-vspackage"></a>Přístup k stránkám možností z jiného balíčku VSPackage
 VSPackage, který hostuje a spravuje stránku možností lze programově přistupovat z jiného VSPackage pomocí modelu automatizace. Například v následujícím kódu je VSPackage registrován jako hostitel stránky možností.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Následující fragment kódu získá hodnotu OptionInteger z MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Když <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atribut zaregistruje stránku možností, stránka je registrována `SupportsAutomation` pod klíčem AutomationProperties, pokud je `true`argument atributu . Automatizace zkontroluje tuto položku registru najít přidružené VSPackage a automatizace pak přistupuje k vlastnosti prostřednictvím stránky hostované možnosti, v tomto případě moje mřížka stránky.

 Cesta registru automation vlastnost je určena <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>kombinací , slovo, AutomationProperties a možnosti stránky kategorie a název. Pokud má například stránka možností kategorii Moje kategorie, název Stránky mřížky a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, pak má vlastnost automation klíč registru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\Moje kategorie\Moje stránka mřížky.

> [!NOTE]
> Kanonický název Stránka mřížky Category.My je hodnota podklíče Název tohoto klíče.
