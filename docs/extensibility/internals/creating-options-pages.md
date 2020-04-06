---
title: Vytváření stránek s možnostmi | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709153"
---
# <a name="create-options-pages"></a>Vytvořit stránky možností
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rámci spravovaného <xref:Microsoft.VisualStudio.Shell.DialogPage> balíčku třídy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odvozené z rozšíření ide přidáním **možnosti** stránky v nabídce **Nástroje.**

 Objekt implementující danou stránku **Možnost imitace** <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> je přidružen k určitým objektům VSPackages.

 Vzhledem k tomu, že prostředí konkretizuje objekt implementující určitou stránku **Možnosti nástrojů,** když je tato konkrétní stránka zobrazena ide:

- A **Tools Option** stránka by měla být implementována na vlastní objekt a nikoli na objekt u implementující VSPackage.

- Objekt nemůže implementovat více stránek **Možnosti nástroje.**

## <a name="register-as-a-tools-options-page-provider"></a>Zaregistrovat se jako zprostředkovatel stránky Možnosti nástrojů
 VSPackage podporující konfiguraci uživatele prostřednictvím stránek **Možnosti nástroje** označuje objekty, které <xref:Microsoft.VisualStudio.Shell.Package> poskytují tyto stránky **Možnosti nástroje** použitím instancí <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> aplikovaných na implementaci.

 Musí existovat jedna <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> instance <xref:Microsoft.VisualStudio.Shell.DialogPage>pro každý odvozený typ, který implementuje tools **options** stránku.

 Každá instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> používá typ, který implementuje stránku **Možnosti nástrojů,** řetězce, které obsahují kategorii a podkategorii použitou k identifikaci stránky **Možnosti nástrojů,** a informace o prostředcích k registraci typu jako stránky **Možnosti nástrojů.**

## <a name="persist-tools-options-page-state"></a>Stav stránky Zachovat možnosti nástroje
 Pokud je implementace stránky **Možnosti nástroje** registrována s povolenou podporou automatizace, ide zachová stav stránky spolu se **všemi ostatními stránkami Možnosti nástroje.**

 A VSPackage můžete spravovat své <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>vlastní trvalost pomocí . Měla by být použita pouze jedna nebo druhá metoda perzistence.

## <a name="implement-dialogpage-class"></a>Implementovat třídu DialogPage
 Objekt poskytující implementaci <xref:Microsoft.VisualStudio.Shell.DialogPage>typu Odvozený v balíčku VSPackage může využít následující zděděné funkce:

- Výchozí okno uživatelského rozhraní.

- Výchozí mechanismus trvalosti <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> k dispozici buď, pokud <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> je použita `true` pro <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> třídu, nebo pokud je vlastnost nastavena na pro, který je použit pro třídu.

- Podpora automatizace.

  Minimální požadavek pro objekt implementující stránku **Možnosti nástroje** pomocí <xref:Microsoft.VisualStudio.Shell.DialogPage> je přidání veřejných vlastností.

  Pokud je třída správně zaregistrována jako zprostředkovatel stránky **Možnosti nástroje,** jsou její veřejné vlastnosti k dispozici v části **Možnosti** v nabídce **Nástroje** ve formě mřížky vlastností.

  Všechny tyto výchozí funkce lze přepsat. Například k vytvoření složitější uživatelské rozhraní vyžaduje pouze přepsání výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>aplikace .

## <a name="example"></a>Příklad
 Co bude následovat, je jednoduchý "Hello world" implementace možnosti stránky. Přidání následujícího kódu do výchozího projektu vytvořeného šablonou balíčku sady Visual Studio s vybranou volbou **Příkaz nabídky** dostatečně demonstruje funkce stránky možností.

### <a name="description"></a>Popis
 Následující třída definuje minimální stránku možností "Hello world". Při otevření může uživatel nastavit `HelloWorld` veřejnou vlastnost v mřížce vlastností.

### <a name="code"></a>kód
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Popis
 Použití následující atribut na třídu balíčku zpřístupní stránku možností při načtení balíčku. Čísla jsou libovolná ID prostředků pro kategorii a stránku a logická hodnota na konci určuje, zda stránka podporuje automatizaci.

### <a name="code"></a>kód
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Popis
 Následující obslužná rutina události zobrazí výsledek v závislosti na hodnotě vlastnosti nastavené na stránce možností. Používá metodu <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> s výsledkem explicitně přetypované do typu vlastní možnost stránky pro přístup k vlastnostem vystavené na stránce.

 V případě projektu generovaného šablonou balíčku voláním této `MenuItemCallback` funkce z funkce ji připojte k výchozímu příkazu přidanému do nabídky **Nástroje.**

### <a name="code"></a>kód
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Viz také
- [Rozšíření uživatelských nastavení a možností](../../extensibility/extending-user-settings-and-options.md)
- [Podpora automatizace pro stránky možností](../../extensibility/internals/automation-support-for-options-pages.md)
