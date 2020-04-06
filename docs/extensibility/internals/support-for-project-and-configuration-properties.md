---
title: Podpora vlastností projektu a konfigurace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704905"
---
# <a name="support-for-project-and-configuration-properties"></a>Podpora vlastností projektu a konfigurace
Okno **Vlastnosti** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v integrovaném vývojovém prostředí (IDE) může zobrazit vlastnosti projektu a konfigurace. Můžete zadat stránku vlastností pro vlastní typ projektu, aby uživatel mohl nastavit vlastnosti pro vaši aplikaci.

 Výběrem uzlu projektu v **Průzkumníku řešení** a následným klepnutím na **příkaz Vlastnosti** v nabídce **Projekt** můžete otevřít dialogové okno obsahující vlastnosti projektu a konfigurace. V [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]písmenech a) a c) a typech projektů odvozených z těchto jazyků se toto dialogové okno zobrazí jako stránka s kartami v [dialogovém okně Obecné, Prostředí a Možnosti](../../ide/reference/general-environment-options-dialog-box.md). Další informace naleznete [v tématu Not in Build: Návod: Vystavení vlastností projektu a konfigurace (C#).](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)

 Architektura spravovaného balíčku pro projekty (MPFProj) poskytuje pomocné třídy pro vytváření a správu nového systému projektu. Zdrojový kód a pokyny pro kompilaci najdete na [mpf pro projekty - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Trvalosti vlastností projektu a konfigurace
 Vlastnosti projektu a konfigurace jsou trvalé v souboru projektu, který má libovolnou příponu názvu souboru přidruženou k typu projektu, například .csproj, .vbproj a .myproj. Jazykové projekty obvykle používají soubor šablony ke generování souboru projektu. Ve skutečnosti však existuje několik způsobů, jak přidružit typy projektů a šablony. Další informace naleznete v [tématu Popis adresáře šablony (. Vsdir) Soubory](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Vlastnosti projektu a konfigurace jsou vytvořeny přidáním položek do souboru šablony. Tyto vlastnosti jsou pak k dispozici pro všechny projekty vytvořené pomocí typu projektu, který používá tuto šablonu. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]projekty a MPFProj oba použít [není v sestavení: MSBuild Přehled](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) schéma pro soubory šablon. Tyto soubory mají PropertyGroup oddíl pro každou konfiguraci. Vlastnosti projektů jsou obvykle trvalé v první propertygroup části, která má argument Konfigurace nastavena na nulový řetězec.

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

 V tomto souboru projektu `<Name>` a `<SchemaVersion>` `<Optimize>` jsou vlastnosti projektu a je vlastnost konfigurace.

 Je odpovědností projektu zachovat vlastnosti projektu a konfigurace souboru projektu.

> [!NOTE]
> Projekt může optimalizovat trvalost tím, že uchovává pouze hodnoty vlastností, které se liší od výchozích hodnot.

## <a name="support-for-project-and-configuration-properties"></a>Podpora vlastností projektu a konfigurace
 Třída `Microsoft.VisualStudio.Package.SettingsPage` implementuje stránky vlastností projektu a konfigurace. Výchozí implementace `SettingsPage` nabízí veřejné vlastnosti uživateli v mřížce obecných vlastností. Metoda `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` vybere třídy odvozené z `SettingsPage` pro mřížky vlastností projektu. Metoda `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` vybere třídy odvozené z `SettingsPage` pro mřížky vlastností konfigurace. Typ projektu by měl přepsat tyto metody vybrat příslušné stránky vlastností.

 Třída `SettingsPage` a `Microsoft.VisualStudio.Package.ProjectNode` třída nabízejí tyto metody k zachování vlastností projektu a konfigurace:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`a `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` zachovat vlastnosti projektu.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`a `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` zachovat vlastnosti konfigurace.

  > [!NOTE]
  > Implementace `Microsoft.VisualStudio.Package.SettingsPage` a `Microsoft.VisualStudio.Package.ProjectNode` třídy používají `Microsoft.Build.BuildEngine` (MSBuild) metody získat a nastavit vlastnosti projektu a konfigurace ze souboru projektu.

  Třída, kterou `SettingsPage` odvozujete, musí implementovat `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` a `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` zachovat vlastnosti projektu nebo konfigurace souboru projektu.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute a cesta registru
 Třídy odvozené z `SettingsPage` jsou navrženy tak, aby byly sdíleny mezi VSPackages. Chcete-li, aby VSPackage vytvořit třídu `SettingsPage`odvozenou `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` z , přidejte `Microsoft.VisualStudio.Shell.Package`do třídy odvozené z .

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 VSPackage, ke kterému je přiřazen atribut není důležité. Při VSPackage je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]registrována s , id třídy (CLSID) libovolný objekt, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> který lze vytvořit je registrovántak, že volání můžete vytvořit.

 Cesta registru objektu, který lze vytvořit, <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>je určena kombinací , slova, identifikátoru CLSID a identifikátoru GUID typu objektu. Pokud `MyProjectPropertyPage` má třída identifikátor {3c693da2-5bca-49b3-bd95-ffe0a39dd723} a userregistryroot je HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, Cesta registru by pak byla HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Atributy a rozložení vlastností projektu a konfigurace
 <xref:System.ComponentModel.CategoryAttribute>Atributy <xref:System.ComponentModel.DisplayNameAttribute>, <xref:System.ComponentModel.DescriptionAttribute> a určují rozložení, popisky a popis vlastností projektu a konfigurace na stránce obecných vlastností. Tyto atributy určují kategorii, zobrazovaný název a popis možnosti.

> [!NOTE]
> Ekvivalentní atributy, SRCategory, LocDisplayName a SRDescription, použít prostředky řetězce pro lokalizaci a jsou definovány v [MPF pro projekty - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Předpokládejme následující fragment kódu:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 Vlastnost `MyConfigProp` konfigurace se zobrazí na stránce vlastností konfigurace jako **vlastnost Moje konfigurace** v kategorii Moje **kategorie**. Pokud je tato volba vybraná, zobrazí se v panelu popis popis popisný popis. **My Description**

## <a name="see-also"></a>Viz také
- [Přidávání a odebírání stránek vlastností](../../extensibility/adding-and-removing-property-pages.md)
- [Projekty](../../extensibility/internals/projects.md)
- [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
