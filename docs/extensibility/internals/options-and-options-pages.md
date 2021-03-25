---
title: Stránky možností a možností | Microsoft Docs
description: Přečtěte si o podpoře pro stránky možnosti, které umožňují změnit hodnoty možností, které určují stav balíčku VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b6c5810cd95b50a63f32cfaa6123e81e35a4be9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063029"
---
# <a name="options-and-options-pages"></a>Možnosti a stránky Možnosti
Kliknutím na **Možnosti** v nabídce **nástroje** otevřete dialogové okno **Možnosti** . Možnosti v tomto dialogovém okně se souhrnně označují jako stránky možností. Ovládací prvek strom v navigačním podokně obsahuje kategorie možností a každá kategorie obsahuje stránky možností. Když vyberete stránku, zobrazí se její možnosti v pravém podokně. Tyto stránky umožňují změnit hodnoty možností, které určují stav balíčku VSPackage.

## <a name="support-for-options-pages"></a>Podpora pro stránky možností
 <xref:Microsoft.VisualStudio.Shell.Package>Třída poskytuje podporu pro vytváření stránek možností a kategorií možností. <xref:Microsoft.VisualStudio.Shell.DialogPage>Třída implementuje stránku možností.

 Výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage> nabídky nabízí veřejné vlastnosti pro uživatele v obecné mřížce vlastností. Toto chování můžete přizpůsobit přepsáním různých metod na stránce a vytvořením vlastní stránky možnosti, která má vlastní uživatelské rozhraní (UI). Další informace najdete v tématu [Vytvoření stránky možností](../../extensibility/creating-an-options-page.md).

 <xref:Microsoft.VisualStudio.Shell.DialogPage>Třída implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager> , která poskytuje stálost pro stránky možností a také pro uživatelská nastavení. Výchozí implementace <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metod a trvalé změny vlastností v registru, pokud je možné vlastnost převést na nebo z řetězce.

## <a name="options-page-registry-path"></a>Možnosti cesty k registru stránky možností
 Ve výchozím nastavení se cesta registru vlastností spravovaných pomocí stránky možnosti určuje kombinací <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , slovem třídy DialogPage a názvem typu třídy stránky možnosti. Například třída stránky možnosti může být definována následujícím způsobem.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Pokud <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> je HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, pak dvojice název vlastnosti a hodnota jsou podklíče HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Cesta registru samotné stránky možností je určena kombinací <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , slovem, ToolsOptionsPages a kategoriemi a názvem stránky možností. Pokud má například stránka vlastní možnosti kategorii, moji stránku možností a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> je HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, pak stránka Možnosti obsahuje klíč registru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Nástroje a možnosti – atributy a rozložení stránky
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Atribut určuje seskupení stránek vlastních možností do kategorií v navigační stromové struktuře dialogového okna **Možnosti** . <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Atribut přidruží stránku možností ke VSPackage, který poskytuje rozhraní. Předpokládejme následující fragment kódu:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Tato deklarace deklaruje, že MyPackage poskytuje dvě stránky možností, OptionsPageGeneral a OptionsPageCustom. V dialogovém okně **Možnosti** se obě stránky možností zobrazují v kategorii **Moje stránky** možností jako **Obecné** a **vlastní**.

## <a name="option-attributes-and-layout"></a>Atributy a rozložení možností
 Uživatelské rozhraní (UI), které stránka poskytuje, určuje vzhled možností na stránce s vlastními možnostmi. Rozložení, popisky a popis možností na stránce Obecné možnosti jsou určeny následujícími atributy:

- <xref:System.ComponentModel.CategoryAttribute> Určuje kategorii možnosti.

- <xref:System.ComponentModel.DisplayNameAttribute> Určuje zobrazovaný název možnosti.

- <xref:System.ComponentModel.DescriptionAttribute> Určuje popis možnosti.

  > [!NOTE]
  > Ekvivalentní atributy, SRCategory, LocDisplayName a SRDescription, používají řetězcové prostředky pro lokalizaci a jsou definovány v [ukázce spravovaného projektu](/azure/devops/integrate/index).

  Předpokládejme následující fragment kódu:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Možnost OptionInteger se zobrazí na stránce možnosti jako **typ Integer** v kategorii **Moje možnosti** . Pokud je vybraná možnost, zobrazí se v poli Popis možnost popis, **Moje celočíselná hodnota**.

## <a name="accessing-options-pages-from-another-vspackage"></a>Přístup ke stránkám možností z jiného balíčku VSPackage
 VSPackage, který hostuje a spravuje stránku možností, lze programově přistupovat z jiného VSPackage pomocí modelu automatizace. Například v následujícím kódu je VSPackage zaregistrován jako hostující stránka možností.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Následující fragment kódu získá hodnotu OptionInteger z MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Když <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atribut zaregistruje stránku možností, je stránka registrována v klíči vlastnosti automatizace, pokud `SupportsAutomation` je argument atributu `true` . Automatizace prověřuje tuto položku registru za účelem nalezení přidruženého VSPackage a Automation pak přistupuje k vlastnosti prostřednictvím stránky hostované možnosti, v tomto případě na stránce mřížka.

 Cesta k registru vlastnosti Automation je určena kombinací <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , slovem, vlastnosti automatizace a kategoriemi a názvem stránky možností. Pokud má například stránka Options kategorii Moje kategorie, název stránky moje mřížka a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, má vlastnost Automation klíč registru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> Stránka kanonický název, my Category.My Grid, je hodnota podklíče názvu tohoto klíče.
