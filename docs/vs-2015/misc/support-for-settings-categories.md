---
title: Podpora pro kategorie nastavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: jillfra
ms.openlocfilehash: 15a3896f8a2010a063393d3a11c1ed3453a008d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689096"
---
# <a name="support-for-settings-categories"></a>Podpora pro kategorie nastavení
Kategorie nastavení se skládá ze skupiny možností, které přizpůsobují integrované vývojové prostředí (IDE). Nastavení může například řídit rozložení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oken a obsah nabídek. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 V nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** a spusťte **Průvodce importem a exportem nastavení**. Průvodce nabízí tři možnosti: export, import nebo resetování nastavení. Výběrem možnosti Exportovat můžete například otevřít stránku průvodce **zvolit nastavení pro export** .  
  
 Ovládací prvek strom v navigačním podokně této stránky uvádí kategorie. Kategorie je skupina souvisejících nastavení, která se zobrazí jako "vlastní bod nastavení", tj. jako zaškrtávací políčko. Tato zaškrtávací políčka slouží k výběru kategorií, které mají být uchovány v souboru. vsettings. Průvodce vám umožní pojmenovat soubor. vsettings a zadat jeho cestu.  
  
> [!NOTE]
> Nastavení jsou uložena nebo obnovena jako kategorie a jednotlivé názvy nastavení nejsou v průvodci zobrazeny.  
  
 Rozhraní Managed Package Framework (MPF) podporuje vytváření kategorií nastavení s minimálním počtem dalších kódů.  
  
- Vytvoříte VSPackage k poskytnutí kontejneru pro kategorii podle <xref:Microsoft.VisualStudio.Shell.Package> třídy.  
  
- Můžete vytvořit kategorii, která je odvozena z <xref:Microsoft.VisualStudio.Shell.DialogPage> třídy.  
  
- Spojíte tyto dvě s <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .  
  
## <a name="support-for-settings-categories"></a>Podpora pro kategorie nastavení  
 <xref:Microsoft.VisualStudio.Shell.Package>Třída poskytuje podporu pro vytváření kategorií. <xref:Microsoft.VisualStudio.Shell.DialogPage>Třída implementuje kategorii. Výchozí implementace nástroje <xref:Microsoft.VisualStudio.Shell.DialogPage> nabízí jeho veřejné vlastnosti uživateli jako kategorii. Další informace najdete v tématu [Vytvoření kategorie nastavení](../extensibility/creating-a-settings-category.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>Třída implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager> , která poskytuje stálost pro obě stránky možností a nastavení uživatelů. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>Metody a <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> uchovávají nastavení do souboru. vssettings, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje jako nebo v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> uvedeném pořadí. <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A>Metoda obnoví nastavení na výchozí hodnoty.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>Třída poskytuje implementaci <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> metody, která čte páry název-hodnota z kanálu XML a pomocí reflexe zjistí veřejné vlastnosti v <xref:Microsoft.VisualStudio.Shell.DialogPage> odvozené třídě. Pro vlastnosti, které mají názvy shodné s páry název-hodnota, jsou předány odpovídající hodnoty.  
  
 Výchozí implementace nástroje <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> používá reflexi pro zjištění veřejných vlastností v <xref:Microsoft.VisualStudio.Shell.DialogPage> odvozené třídě a zápis názvů vlastností a hodnot do kanálu XML jako páry název-hodnota.  
  
### <a name="settings-category-registry-path"></a>Cesta k registru kategorií nastavení  
 Cesta registru kategorie nastavení je určena kombinací <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , slovem, UserSettings, kategorií nastavení a názvem vlastního bodu nastavení. Názvy kategorie nastavení a vlastní bod nastavení jsou spojeny a odděleny podtržítkem pro vytvoření kanonického, nelokalizovaného názvu, který se zobrazí v registru. Pokud je například kategorie nastavení "Moje kategorie", název bodu vlastního nastavení "Moje nastavení" a ApplicationRegistryRoot HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, pak kategorie nastavení obsahuje klíč registru HKEY_LOCAL_MACHINE nastavení \SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My.  
  
> [!NOTE]
> Kanonický název se nezobrazuje v uživatelském rozhraní (UI). Slouží k přidružení čitelného názvu k kategorii nastavení, podobně jako programový identifikátor (ProgID).  
  
### <a name="settings-category-attribute"></a>Atribut kategorie nastavení  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Určuje mapování kategorií na body vlastního nastavení v **Průvodci importem a exportem nastavení** tím, že přidruží kategorii k VSPackage, která je poskytuje. Předpokládejme následující fragment kódu:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 ID prostředku 106 se mapuje na moji kategorii, 107 na moje nastavení a 108 na různé možnosti. Tato deklarace deklaruje, že `MyPackage` poskytuje kategorii, nastavení Category_My. Kategorie je poskytována `OptionsPageGeneral` třídou, která musí implementovat <xref:Microsoft.VisualStudio.Shell.IProfileManager> . Nastavení v této kategorii jsou veřejné vlastnosti `OptionsPageGeneral` třídy.  
  
 V **Průvodci importem a exportem nastavení**má bod nastavení název, moje nastavení. Když je vybraný bod nastavení, zobrazí se popis, **různé možnosti**. Název a popis bodu nastavení jsou odebírány z lokalizovaných řetězcových prostředků.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření stránky možnosti](../extensibility/creating-an-options-page.md)   
 [Ukázky VSSDK](../misc/vssdk-samples.md)   
 [Stav VSPackage](../misc/vspackage-state.md)   
 [Přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)