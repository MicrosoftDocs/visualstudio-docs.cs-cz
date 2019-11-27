---
title: Co je nového ve Visual Studio 2015 SDK | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6735f929f52387f4cb40406d6918894e72bb40d3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299688"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Co&#39;nového ve Visual Studio 2015 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK obsahuje následující nové a aktualizované funkce pro Visual Studio 2015, Visual Studio 2015, aktualizovat a Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Spouští se v sadě Visual Studio 2017, vyhledávání vlastních projektů a šablon položek už se provede. Rozšíření místo toho musíte zadat soubory manifestu šablon, které popisují umístění instalace služby tyto šablony. Visual Studio 2017 můžete použít k aktualizaci rozšíření VSIX. Pokud provádíte nasazení vašeho rozšíření pomocí MSI, musíte soubory manifestu šablony vygenerovat ručně. Další informace najdete v tématu [Upgrade vlastních šablony projektů a položek pro Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schéma manifestu šablony je dokumentováno v [referenčních informacích o schématu manifestu šablony sady Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1
 Aktualizace Update 1 zahrnuje nástroje, které pomáhají vaše rozšíření fungovat dobře s barevné motivy a image služby Visual Studio.

 Tato témata najdete v části [nástroje VSSDK](../extensibility/internals/vssdk-utilities.md) :

- [Nástroje Color Color Tools](../extensibility/internals/color-theming-tools.md) vám pomůžou vytvořit a upravit vlastní barvy pro Visual Studio.

- [Nástroje Image Service](../extensibility/internals/image-service-tools.md) umožňují pracovat se soubory manifestu sady Visual Studio image.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nový způsob, jak přidat sady Visual Studio SDK do sady Visual Studio
 Spouští se v sadě Visual Studio 2015, není nutné samostatně stáhnout Visual Studio SDK. Místo toho ho můžete nainstalovat jako součást procesu instalace normální, nebo můžete nainstalovat později. Když otevřete nebo vytvořte VSIX řešení sady Visual Studio vás vyzve k instalaci Visual Studio Extensibility Tools. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nové způsoby vytváření rozšíření
 Od verze Visual Studio 2015 SDK, budete mít různé možnosti pro vytvoření rozšíření, v závislosti na programovacím jazyku, který používáte.

### <a name="visual-c-and-visual-basic"></a>Visual C# a Visual Basic
 Pro C# a Visual Basic je plný rozsah šablony položek projektu, které vám umožňují vytvářet rozšíření VSPackages, příkazy nabídky, okna nástrojů, editor třídění, vylepšení editoru a rozšíření okraj editoru. Můžete přidat některé nebo všechny z nich standardní projektu VSIX. Další informace naleznete v tématu:

- [Vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Vytváření rozšíření pomocí VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Průvodce vytvořením balíčku VSPackage už vytvoří rozšíření v jazyce C# nebo Visual Basic.

### <a name="c"></a>C++
 Průvodce vytvořením balíčku VSPackage jazyka C++, podporují příkazy nabídky, panely nástrojů a vlastních editorech. Vyhledejte ho v dialogovém okně **Nový projekt** v dialogu **Visual C++ nebo rozšiřitelnost**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Odkaz na sestavení SDK VS prostřednictvím balíčku NuGet
 Kvůli vyšší přenositelnosti a sdílení projektů rozšiřitelnosti můžete použít verze NuGet referenčních sestavení sady SDK pro VS.  Ty jsou k dispozici v [NuGet.org](https://www.nuget.org/) publikovaných pomocí [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) a lze je snadno přidat do projektu nebo řešení prostřednictvím dialogu sady Visual Studio **References/spravovat balíčky NuGet** . Můžete přidat jednotlivé odkazy na konkrétní rozšiřitelná sestavení nebo přidat všechna sestavení sady VS SDK k odkazování pomocí [meta balíčku](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)sady vs SDK. Další informace o NuGet najdete v tématu [Přehled NuGet](https://docs.microsoft.com/nuget/) a [Správa balíčků NuGet pomocí tohoto dialogového okna](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).

 Při použití verze NuGet referenčních sestavení sady SDK pro VS jiný uživatel nemusí nainstalovat sadu SDK pro VS a otevřete svůj projekt sestavit.  NuGet referenčních sestavení a nástroje sestavení sady SDK pro VS automaticky se nainstaluje v jejich počítači pro daný projekt.

 Šablony položek VS SDK použít NuGet pro jejich odkazů a vytváření buildů, takže získáte výhody NuGet ve výchozím nastavení.

> [!NOTE]
> Můžete pokračovat v používání referenčních sestavení sady VS SDK s vašimi projekty (nacházející se v \<umístění instalace sady Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) a stávající projekty rozšiřitelnosti nemusíte upgradovat, aby používaly balíčky NuGet.  Dialog **odkazy projektu/přidat odkaz** i nadále používají referenční sestavení nainstalovaná v sadě vs SDK.
>
> Chcete-li upravit existující projekty pro použití NuGet, přečtěte si téma [How to: migrace VSPackages do sady Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) , které obsahuje část o aktualizaci rozšiřujících projektů na balíčky NuGet.

## <a name="light-bulbs"></a>Ikony žárovky
 Poskytuje jednu z nejzajímavějších nové způsoby psaní kódu rozšíření projektu Roslyn. Další informace najdete v tématu [Roslyn](https://github.com/dotnet/Roslyn).

 Ikony žárovky jsou novou funkci, která se dodává s VSSDK. Jsou ikony používané v editoru sady Visual Studio, které se rozbalí a zobrazí sadu akcí refaktoringu kódu nebo opravy problémů, které jsou identifikované analyzátorů integrované kódu. Další informace najdete v tématu [Návod: zobrazení návrhů](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)žárovky.

## <a name="updated-user-experience-guidelines"></a>Pokyny k aktualizované uživatelské prostředí
 Navrhování nového rozšíření nebo funkcí pro Visual Studio? Podívejte se na aktualizované a rozšířené [pokyny pro uživatelské prostředí sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Najdete [tokeny barev](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [velikosti písem](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specifikace rozložení dialogů](../extensibility/ux-guidelines/layout-for-visual-studio.md)a další pokyny, které potřebujete k bezproblémové integraci nového uživatelského rozhraní se sadou Visual Studio.
