---
title: Podpora vlastností projektu a konfigurace | Microsoft Docs
description: Naučte se, jak poskytnout stránku vlastností pro vlastní typ projektu v integrovaném vývojovém prostředí sady Visual Studio, které může zobrazit rozšířené vlastnosti projektu a konfigurace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0c5ac6cf82d39790fa2d7762fea6b711a546da24
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080746"
---
# <a name="support-for-project-and-configuration-properties"></a>Podpora vlastností projektu a konfigurace
Okno **vlastnosti** v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE) může zobrazit vlastnosti projektu a konfigurace. Můžete zadat stránku vlastností pro vlastní typ projektu, aby uživatel mohl nastavit vlastnosti pro vaši aplikaci.

 Výběrem uzlu projektu v **Průzkumník řešení** a následným kliknutím na **vlastnosti** v nabídce **projekt** můžete otevřít dialogové okno, které obsahuje vlastnosti projektu a konfigurace. V [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typy projektů odvozených z těchto jazyků se toto dialogové okno zobrazí jako stránka s kartami v [dialogovém okně Obecné, prostředí, možnosti](../../ide/reference/general-environment-options-dialog-box.md). Další informace naleznete v tématu [Not in Build: Názorný postup: vystavení vlastností projektu a konfigurace (C#)](/previous-versions/bb166517(v=vs.100)).

 Managed Package Framework for Projects (MPFProj) poskytuje pomocné třídy pro vytváření a správu systému nových projektů. Zdrojový kód a pokyny k kompilaci najdete na stránce [MPF pro projekty – Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Trvalost vlastností projektu a konfigurace
 Vlastnosti projektu a konfigurace jsou trvalé v souboru projektu, který má libovolnou příponu názvu souboru přidruženou k typu projektu, například. csproj,. vbproj a. myproj. Jazykové projekty obvykle používají soubor šablony k vygenerování souboru projektu. Existuje však několik způsobů, jak přidružit typy projektů a šablony. Další informace najdete v tématu [Popis adresáře šablon (. VSDIR) soubory](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Vlastnosti projektu a konfigurace jsou vytvořeny přidáním položek do souboru šablony. Tyto vlastnosti jsou následně k dispozici pro všechny projekty vytvořené pomocí typu projektu, který používá tuto šablonu. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projekty a MPFProj používají pro soubory šablon schéma, které [není v sestavách sestavení: MSBuild Overview](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) . Tyto soubory mají oddíl Property pro každou konfiguraci. Vlastnosti projektů jsou obvykle trvale uložené v první části skupiny vlastností, která má argument konfigurace nastavený na řetězec s hodnotou null.

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

 V tomto souboru projektu `<Name>` a `<SchemaVersion>` jsou vlastnosti projektu a `<Optimize>` je konfigurační vlastnost.

 Projekt je zodpovědný za zachování vlastností projektu a konfigurace souboru projektu.

> [!NOTE]
> Projekt může optimalizovat trvalost tím, že uchová pouze hodnoty vlastností, které se liší od jejich výchozích hodnot.

## <a name="support-for-project-and-configuration-properties"></a>Podpora vlastností projektu a konfigurace
 `Microsoft.VisualStudio.Package.SettingsPage`Třída implementuje stránky vlastností projektu a konfigurace. Výchozí implementace nástroje `SettingsPage` nabízí veřejné vlastnosti uživateli v mřížce obecných vlastností. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`Metoda vybere třídy odvozené z `SettingsPage` pro mřížky vlastností projektu. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`Metoda vybere třídy odvozené z `SettingsPage` pro mřížky vlastností konfigurace. Typ projektu by měl přepsat tyto metody a vybrat tak příslušné stránky vlastností.

 `SettingsPage`Třída a `Microsoft.VisualStudio.Package.ProjectNode` Třída nabízí tyto metody pro zachování vlastností projektu a konfigurace:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` a `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` trvalé vlastnosti projektu.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` a `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` Zachovat vlastnosti konfigurace.

  > [!NOTE]
  > Implementace `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` tříd a používají `Microsoft.Build.BuildEngine` metody (MSBuild) k získání a nastavení vlastností projektu a konfigurace ze souboru projektu.

  Třída, která je odvozena z `SettingsPage` musí implementovat `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` a `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` pro trvalé vlastnosti projektu nebo konfigurace souboru projektu.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute a cesta k registru
 Třídy odvozené od `SettingsPage` jsou navržené tak, aby se sdílely napříč VSPackage. Chcete-li, aby VSPackage mohl vytvořit třídu odvozenou z `SettingsPage` , přidejte `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` do třídy odvozené z `Microsoft.VisualStudio.Shell.Package` .

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 VSPackage, ke kterému je atribut připojen, je neimportovaná. Je-li VSPackage zaregistrován s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , identifikátor třídy (CLSID) libovolného objektu, který lze vytvořit, je registrován tak, aby bylo volání <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> možné ho vytvořit.

 Cesta registru objektu, který lze vytvořit, je určena kombinací <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , slovem, identifikátorem CLSID a identifikátorem GUID typu objektu. Pokud `MyProjectPropertyPage` má třída identifikátor GUID {3c693da2-5bca-49b3-bd95-ffe0a39dd723} a UserRegistryRoot je HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, cesta k registru by byla HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Atributy a rozložení vlastností projektu a konfigurace
 <xref:System.ComponentModel.CategoryAttribute>Atributy, <xref:System.ComponentModel.DisplayNameAttribute> a <xref:System.ComponentModel.DescriptionAttribute> určují rozložení, popisky a popis vlastností projektu a konfigurace na stránce Obecné vlastnosti. Tyto atributy určují kategorii, zobrazovaný název a Popis možnosti v uvedeném pořadí.

> [!NOTE]
> Ekvivalentní atributy, SRCategory, LocDisplayName a SRDescription, používají řetězcové prostředky pro lokalizaci a jsou definovány v atributu [MPF pro projekty – Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Předpokládejme následující fragment kódu:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 `MyConfigProp`Vlastnost Configuration se zobrazí na stránce vlastností konfigurace jako **vlastnost moje** konfigurace v kategorii kategorie, **Moje kategorie**. Pokud je vybraná možnost, popis, zobrazí se **Popis, který** se zobrazí na panelu Popis.

## <a name="see-also"></a>Viz také
- [Přidávání a odebírání stránek vlastností](../../extensibility/adding-and-removing-property-pages.md)
- [Projekty](../../extensibility/internals/projects.md)
- [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)