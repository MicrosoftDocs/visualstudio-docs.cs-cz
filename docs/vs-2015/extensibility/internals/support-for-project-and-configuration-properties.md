---
title: Podpora pro projekt a vlastnosti konfigurace | Dokumentace Microsoftu
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
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37c41e4c2074f6bb4896c6ff91ea292c5e21ba81
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760638"
---
# <a name="support-for-project-and-configuration-properties"></a>Podpora vlastností projektu a konfigurace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Vlastnosti** okna [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) můžete zobrazit vlastnosti projektu a konfigurace. Stránky vlastností pro vlastní typ projektu můžete zadat tak, aby uživatel může nastavit vlastnosti pro vaši aplikaci.  
  
 Vyberte uzel projektu v **Průzkumníka řešení** a pak levým na **vlastnosti** na **projektu** nabídku, můžete otevřít dialogové okno, které obsahuje projekt a konfiguraci Vlastnosti. V [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]a typy odvozené z těchto jazyků toto dialogové okno se zobrazí jako stránka s kartami v projektu [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md). Další informace najdete v tématu [není v sestavení: Návod: vystavení projektu a vlastnosti konfigurace (C#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Managed Package Framework pro projekty (MPFProj) poskytuje pomocné třídy pro vytváření a správu nový systém projektů. Zdrojového kódu a kompilace pokyny najdete v [MPF projektů – Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Trvalost projektu a vlastnosti konfigurace  
 Vlastnosti projektu a konfigurace jsou ukládány v souboru projektu, který má příponu názvu souboru spojené s typem projektu, například, .csproj, .vbproj a .myproj. Soubor šablony projektů jazyka obvykle používají ke generování souboru projektu. Existují však skutečně několik způsobů, jak přidružit typy projektů a šablon. Další informace najdete v tématu [NIB: šablony sady Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041) a [popisu adresáře šablon (. Soubory VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Vlastnosti projektu a konfigurace jsou vytvořena přidáním položky do souboru šablony. Tyto vlastnosti jsou pak k dispozici pro libovolný projekt vytvořen pomocí typu projektu, který používá tuto šablonu. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projekty a MPFProj používají [není v sestavení: Přehled nástroje MSBuild](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde) schéma pro soubory šablon. Tyto soubory obsahují PropertyGroup část pro každou konfiguraci. Vlastnosti projektů jsou obvykle zachované v první části PropertyGroup, která má jako argument konfigurace nastavit na prázdný řetězec.  
  
 Následující kód ukazuje začátek základního souboru projektu MSBuild.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 V tomto souboru projektu `<Name>` a `<SchemaVersion>` jsou vlastnosti projektu a `<Optimize>` představují vlastnost konfigurace.  
  
 Je odpovědností se projekt uchová vlastnosti projektu a konfigurace souboru projektu.  
  
> [!NOTE]
>  Projekt můžete optimalizovat trvalost zachování pouze hodnoty vlastností, které se liší od výchozí hodnoty.  
  
## <a name="support-for-project-and-configuration-properties"></a>Podpora vlastností projektu a konfigurace  
 `Microsoft.VisualStudio.Package.SettingsPage` Třída implementuje stránky vlastností projektu a konfigurace. Výchozí implementace `SettingsPage` nabízí veřejné vlastnosti uživatele v mřížce obecných vlastností. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Metoda vybere třídy odvozené od `SettingsPage` pro mřížek vlastností projektu. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Metoda vybere třídy odvozené od `SettingsPage` pro mřížek vlastností konfigurace. Typ projektu by měly přepsat tyto metody k výběru příslušné vlastnosti stránky.  
  
 `SettingsPage` Třídy a `Microsoft.VisualStudio.Package.ProjectNode` třídy nabízí tyto metody se zachovat vlastnosti projektu a konfigurace:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` a `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` zachovat vlastnosti projektu.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` a `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` zachovat vlastnosti konfigurace.  
  
  > [!NOTE]
  >  Implementace `Microsoft.VisualStudio.Package.SettingsPage` a `Microsoft.VisualStudio.Package.ProjectNode` třídy použijte `Microsoft.Build.BuildEngine` (MSBuild) metody pro získání a nastavení vlastností projektu a konfigurace ze souboru projektu.  
  
  Odvozujete od třídy `SettingsPage` musí implementovat `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` a `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` zachovat vlastnosti projektu nebo konfigurace souboru projektu.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute a cesta v registru  
 Třídy odvozené z `SettingsPage` jsou navržené ke sdílení napříč rozšíření VSPackages. Aby bylo možné pro balíček VSPackage pro vytvoření třídy odvozené z `SettingsPage`, přidejte `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` pro třídy odvozené od `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Je důležité sady VSPackage, která je připojena. Když VSPackage zaregistruje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], registrovaný (CLSID) id třídy objektu, který je možné vytvořit tak, aby volání <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> můžete ho vytvořit.  
  
 Objekt, který je možné vytvořit cestu registru je určen tím, že zkombinujete <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, slovo, identifikátor CLSID a identifikátor guid typu objektu. Pokud `MyProjectPropertyPage` třída nemá identifikátor guid {3c693da2-5bca-49b3-bd95-ffe0a39dd723} a UserRegistryRoot je HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, pak by cesta v registru HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Projekt a atributy vlastnosti konfigurace a rozložení  
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, A <xref:System.ComponentModel.DescriptionAttribute> atributy určují, rozložení, označování popisky a popis vlastností projektu a konfigurační stránce obecných vlastností. Tyto atributy určit kategorii, zobrazí název a popis možnosti, v uvedeném pořadí.  
  
> [!NOTE]
>  Ekvivalentní atributy, SRCategory, LocDisplayName a SRDescription, použití řetězcových prostředků pro lokalizaci a jsou definovány v [MPF projektů – Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Předpokládejme následující fragment kódu:  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 `MyConfigProp` Vlastnost konfigurace se zobrazí na stránce vlastností konfigurace jako **Moje konfigurační vlastnost** v kategorii **kategorie Mé**. Pokud je vybraná možnost, popis, **Můj popis**, zobrazí se v panelu Popis.  
  
## <a name="see-also"></a>Viz také  
 [Není v sestavení: Návod: vystavení projektu a vlastnosti konfigurace (C#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Přidávání a odebírání stránek vlastností](../../extensibility/adding-and-removing-property-pages.md)   
 [Stav balíčku VSPackage](../../misc/vspackage-state.md)   
 [Projekty](../../extensibility/internals/projects.md)   
 [NIB: Šablony sady Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

