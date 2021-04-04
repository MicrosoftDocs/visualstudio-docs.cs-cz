---
title: Vytváření stránek možností | Microsoft Docs
description: Naučte se, jak vytvořit stránku možností v nabídce nástroje v aplikaci Visual Studio implementací třídy třídy DialogPage ze spravovaného rozhraní balíčku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7b1b8b92f978739bfa4e540013347e216781cd4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217239"
---
# <a name="create-options-pages"></a>Vytvořit stránky možností
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní spravovaného balíčku třídy odvozené z <xref:Microsoft.VisualStudio.Shell.DialogPage> rozšíření [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE přidáním stránek **Možnosti** v nabídce **nástroje** .

 Objekt, který implementuje danou stránku **možností nástrojů** , je spojen s konkrétními VSPackage pomocí <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objektu.

 Vzhledem k tomu, že prostředí vytvoří instanci objektu implementující určité **Možnosti nástrojů** , když je tato konkrétní stránka zobrazena pomocí rozhraní IDE:

- Stránka **možností nástroje** by měla být implementována na vlastním objektu a nikoli na objektu, který implementuje VSPackage.

- Objekt nemůže implementovat více stránek **možností nástroje** .

## <a name="register-as-a-tools-options-page-provider"></a>Registrovat jako poskytovatele stránky možností nástrojů
 Stránka s podporou nástrojů pro konfiguraci uživatele prostřednictvím **nástrojů stránky možnosti** určuje objekty, které poskytují tyto stránky s **možnostmi nástrojů** pomocí instancí <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> použitých pro <xref:Microsoft.VisualStudio.Shell.Package> implementaci.

 Musí existovat jedna instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pro každý <xref:Microsoft.VisualStudio.Shell.DialogPage> odvozený typ, který implementuje stránku **možností nástrojů** .

 Každá instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> používá typ, který implementuje stránku **Možnosti nástrojů** , řetězce, které obsahují kategorii a podkategorii použitou k identifikaci stránky **možností nástrojů** , a informace o prostředku pro registraci typu jako stránku **možností nástrojů** .

## <a name="persist-tools-options-page-state"></a>Stav stránky možností zachování nástrojů
 Pokud je implementace stránky **Možnosti nástrojů** registrována s povolenou podporou automatizace, rozhraní IDE přetrvá stav stránky společně se všemi ostatními stránkami **možností nástrojů** .

 VSPackage může spravovat vlastní trvalost pomocí <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Měla by se použít jenom jedna nebo jiná metoda trvalosti.

## <a name="implement-dialogpage-class"></a>Implementovat třídu třídy DialogPage
 Objekt, který poskytuje implementaci <xref:Microsoft.VisualStudio.Shell.DialogPage> odvozeného typu VSPackage, může využít následující zděděné funkce:

- Výchozí okno uživatelského rozhraní.

- Výchozí mechanismus trvalosti k dispozici <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> , pokud je použita na třídu, nebo pokud <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> je vlastnost nastavena na `true` pro <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> třídu, která je použita na třídu.

- Podpora automatizace.

  Minimální požadavek pro objekt implementující stránku **možností nástrojů** pomocí <xref:Microsoft.VisualStudio.Shell.DialogPage> je přidání veřejných vlastností.

  Pokud je třída správně registrována jako poskytovatel stránky **možností nástroje** , pak jsou její veřejné vlastnosti k dispozici v části **Možnosti** nabídky **nástroje** ve formě mřížky vlastností.

  Všechny tyto výchozí funkce lze přepsat. Například pro vytvoření propracovanějších uživatelských rozhraní vyžaduje pouze přepsání výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .

## <a name="example"></a>Příklad
 Následuje Jednoduchá implementace "Hello World" na stránce Možnosti. Přidáním následujícího kódu do výchozího projektu vytvořeného šablonou balíčku sady Visual Studio s vybranou možností **příkazu nabídky** budete patřičně předvést funkci stránky možností.

### <a name="description"></a>Description
 Následující třída definuje minimální stránku možností "Hello World". Při otevření může uživatel nastavit `HelloWorld` vlastnost Public v mřížce vlastností.

### <a name="code"></a>Kód
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs" id="Snippet11":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb" id="Snippet11":::

### <a name="description"></a>Description
 Použití následujícího atributu pro třídu Package zpřístupňuje stránku Options při načtení balíčku. Čísla jsou libovolná ID prostředků pro kategorii a stránku a logická hodnota na konci určuje, jestli stránka podporuje automatizaci.

### <a name="code"></a>Kód
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet07":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet07":::

### <a name="description"></a>Description
 Následující obslužná rutina události zobrazí výsledek v závislosti na hodnotě sady vlastností na stránce Možnosti. Používá <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metodu s výsledkem explicitního přetypování do vlastního typu stránky možností pro přístup k vlastnostem vystaveným stránkou.

 V případě projektu generovaného šablonou balíčku zavolejte tuto funkci z `MenuItemCallback` funkce, aby se připojila k výchozímu příkazu přidanému do nabídky **nástroje** .

### <a name="code"></a>Kód
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet08":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet08":::

## <a name="see-also"></a>Viz také
- [Rozšíří uživatelská nastavení a možnosti.](../../extensibility/extending-user-settings-and-options.md)
- [Podpora automatizace pro stránky možností](../../extensibility/internals/automation-support-for-options-pages.md)
