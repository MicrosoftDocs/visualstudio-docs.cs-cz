---
title: Podpora pro kategorie nastavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: douge
ms.openlocfilehash: 53abd3c9f35f16c2f2ae62e2c4f339a86477a8b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244930"
---
# <a name="support-for-settings-categories"></a>Podpora pro kategorie nastavení
Nastavení kategorie se skládá ze skupiny z možností, které přizpůsobení integrovaného vývojového prostředí (IDE). Například nastavení můžete řídit rozložení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] windows a obsah nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Na **nástroje** klikněte na nabídku **nastavení importu a exportu** spustit **Průvodce importem a exportem nastavení**. Průvodce nabízí tři možnosti: exportovat, importovat nebo obnovit nastavení. Výběr export, například se otevře **zvolte nastavení pro Export** stránky průvodce.  
  
 Ovládací prvek stromové struktury v navigačním podokně na této stránce je uvedený seznam kategorií. Kategorie je skupina souvisejících nastavení, které se zobrazí jako "vlastní nastavení bod", tedy jako zaškrtávací políčko. Pomocí těchto zaškrtávacích políček vyberte kategorie, které chcete zachovat v souboru .vsettings. Průvodce vám umožní název souboru .vsettings a zadejte jeho cestu.  
  
> [!NOTE]
>  Nastavení se uloží nebo obnovili kategorii a názvy jednotlivých nastavení nejsou zobrazeny v průvodci.  
  
 Rozhraní spravovaného balíčku (MPF) podporuje vytváření kategorie nastavení minimální další kód.  
  
-   Vytvoření balíčku VSPackage k poskytnutí kontejner pro kategorii tak vytváření podtříd <xref:Microsoft.VisualStudio.Shell.Package> třídy.  
  
-   Vytvořit kategorii, samotný to odvozením z <xref:Microsoft.VisualStudio.Shell.DialogPage> třídy.  
  
-   Připojení s nimi <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="support-for-settings-categories"></a>Podpora pro kategorie nastavení  
 <xref:Microsoft.VisualStudio.Shell.Package> Třída poskytuje podporu pro vytváření kategorie. <xref:Microsoft.VisualStudio.Shell.DialogPage> Třída implementuje kategorii. Výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage> nabízí jeho veřejné vlastnosti uživatele jako kategorie. Další informace najdete v tématu [vytvoření kategorie nastavení](../extensibility/creating-a-settings-category.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Implementuje třída <xref:Microsoft.VisualStudio.Shell.IProfileManager>, která poskytuje trvalosti pro stránky možnosti a nastavení uživatele. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> a <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> metody stávající nastavení do .vssettings souboru, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>v uvedeném pořadí. <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> Metoda resetuje na výchozí hodnoty nastavení.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Třída poskytuje implementaci <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> metodu, která přečte dvojice název hodnota ze souboru xml informačního kanálu a používá reflexi ke zjišťování veřejné vlastnosti v <xref:Microsoft.VisualStudio.Shell.DialogPage> odvozené třídy. Vlastnosti, které mají názvy, které odpovídají dvojice název hodnota jsou uvedeny odpovídající hodnoty.  
  
 Výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> používá reflexi ke zjišťování veřejné vlastnosti v <xref:Microsoft.VisualStudio.Shell.DialogPage> odvozené třídy a zapíše názvy a hodnoty XML informačního kanálu jako dvojice název hodnota.  
  
### <a name="settings-category-registry-path"></a>Cesta v registru kategorie nastavení  
 Cesta v registru nastavení kategorie je určen tím, že zkombinujete <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, slovo UserSettings, kategorie nastavení a název vlastních nastavení bodu. Názvy nastavení kategorie a vlastní nastavení bodu jsou připojené k a oddělená podtržítkem tvořit canonical, nelokalizovaný název, který se zobrazí v registru. Například vlastní nastavení přejděte název "nastavení" a ApplicationRegistryRoot HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp Pokud kategorie nastavení je "My kategorie", a pak nastavení kategorie má klíč registru, HKEY_LOCAL_ MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My nastavení.  
  
> [!NOTE]
>  Název v kanonickém tvaru nezobrazí v uživatelském rozhraní (UI). Je použito k přidružení čitelný název z kategorie nastavení, podobně jako programový identifikátor (ProgID).  
  
### <a name="settings-category-attribute"></a>Atribut kategorie nastavení  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Určuje mapování kategorií, které mají vlastní nastavení okamžiky **Průvodce importem a exportem nastavení** přidruží kategorii sady VSPackage, která ho obsahuje. Předpokládejme následující fragment kódu:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 ID prostředku 106 mapuje na "Můj kategorie", 107 "Nastavení" a "Různé možnosti" 108. Deklaruje, že to `MyPackage` poskytuje kategorie má Category_My nastavení. Do kategorie je poskytován `OptionsPageGeneral` třídu, která musí implementovat <xref:Microsoft.VisualStudio.Shell.IProfileManager>. Veřejné vlastnosti jsou nastavení do této kategorie spadají `OptionsPageGeneral` třídy.  
  
 V **Průvodce importem a exportem nastavení**, nastavení bodu má název, nastavení. Když je vybrán bod nastavení, popis, **různé možnosti**, se zobrazí. Nastavení bodu název a popis pocházejí z prostředků lokalizované řetězce.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření stránky Možnosti](../extensibility/creating-an-options-page.md)   
 [Ukázky VSSDK](../misc/vssdk-samples.md)   
 [Stav balíčku VSPackage](../misc/vspackage-state.md)   
 [Přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)