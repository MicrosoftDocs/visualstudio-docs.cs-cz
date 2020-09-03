---
title: Co je nového v sadě Visual Studio 2015 SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917332"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Co&#39;s novinkou v sadě Visual Studio 2015 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sada Visual Studio SDK obsahuje následující nové a aktualizované funkce pro Visual Studio 2015, Visual Studio 2015 a Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Počínaje verzí sady Visual Studio 2017 již nebude vyhledávání vlastních šablon projektů a položek provedeno. Místo toho musí rozšíření poskytnout soubory manifestu šablony, které popisují umístění instalace těchto šablon. Pomocí sady Visual Studio 2017 můžete aktualizovat rozšíření VSIX. Pokud nasadíte rozšíření pomocí MSI, je nutné vygenerovat soubory manifestu šablony ručně. Další informace najdete v tématu [Upgrade vlastních šablony projektů a položek pro Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schéma manifestu šablony je dokumentováno v [referenčních informacích o schématu manifestu šablony sady Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>Aktualizace sady VS 2015 SDK 1
 Aktualizace 1 obsahuje nástroje, které vaší příponě pomůžou zajistit správnou práci s barevnými motivy a službou image sady Visual Studio.

 Tato témata najdete v části [nástroje VSSDK](../extensibility/internals/vssdk-utilities.md) :

- [Nástroje Color Color Tools](../extensibility/internals/color-theming-tools.md) vám pomůžou vytvořit a upravit vlastní barvy pro Visual Studio.

- [Nástroje Image Service](../extensibility/internals/image-service-tools.md) umožňují pracovat se soubory manifestu sady Visual Studio image.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nový způsob, jak přidat sadu Visual Studio SDK do sady Visual Studio
 Od sady Visual Studio 2015 nemusíte stahovat sadu Visual Studio samostatně. Místo toho ho můžete nainstalovat jako součást normálního instalačního procesu, nebo ho můžete nainstalovat později. Když otevřete nebo vytvoříte řešení VSIX, Visual Studio vás vyzve k instalaci Visual Studio Extensibility Tools. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nové způsoby vytváření rozšíření
 Počínaje sadou Visual Studio 2015 SDK máte různé možnosti pro vytváření rozšíření v závislosti na použitém programovacím jazyce.

### <a name="visual-c-and-visual-basic"></a>Visual C# a Visual Basic
 V jazyce C# a Visual Basic existuje celá škála šablon položek projektu, které umožňují vytvářet VSPackage, příkazy nabídky, okna nástrojů, klasifikátory editoru, doplňky editoru a rozšíření okrajů editoru. Můžete přidat všechny nebo všechny z nich do standardního projektu VSIX. Další informace naleznete v tématu:

- [Vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Vytváření rozšíření pomocí VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Průvodce VSPackage již nevytváří rozšíření v jazyce C# nebo Visual Basic.

### <a name="c"></a>C++
 V jazyce C++ podporuje Průvodce rozhraním VSPackage příkazy nabídky, okna nástrojů a vlastní editory. Vyhledejte ho v dialogovém okně **Nový projekt** v **Visual C++ nebo rozšiřitelnosti**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Referenční sestavení sady VS SDK přes NuGet
 Pro zvýšení přenositelnosti a sdílení projektů rozšíření můžete použít verze NuGet referenčních sestavení sady VS SDK.  Ty jsou k dispozici v [NuGet.org](https://www.nuget.org/) publikovaných pomocí [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) a lze je snadno přidat do projektu nebo řešení prostřednictvím dialogu sady Visual Studio **References/spravovat balíčky NuGet** . Můžete přidat jednotlivé odkazy na konkrétní rozšiřitelná sestavení nebo přidat všechna sestavení sady VS SDK k odkazování pomocí [meta balíčku](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)sady vs SDK. Další informace o NuGet najdete v tématu [Přehled NuGet](/nuget/) a [Správa balíčků NuGet pomocí tohoto dialogového okna](/nuget/consume-packages/install-use-packages-visual-studio).

 Použijete-li verze NuGet referenčních sestavení sady VS SDK, jiný uživatel není muset instalovat sadu VS SDK, aby bylo možné projekt otevřít a sestavit.  Referenční sestavení NuGet a nástroje VS SDK Build jsou automaticky nainstalovány do svého počítače pro daný projekt.

 Šablony sady VS SDK používají NuGet pro své odkazy a nástroje sestavení, takže ve výchozím nastavení získáte výhody NuGetu.

> [!NOTE]
> Můžete pokračovat v používání referenčních sestavení sady VS SDK s vašimi projekty (nacházející se pod \<Visual Studio Install Location> \ VSSDK\VisualStudioIntegration\Common\Assemblies) a stávající projekty rozšiřitelnosti nemusíte upgradovat, aby používaly balíčky NuGet.  Dialog **odkazy projektu/přidat odkaz** i nadále používají referenční sestavení nainstalovaná v sadě vs SDK.
>
> Chcete-li upravit existující projekty pro použití NuGet, přečtěte si téma [How to: migrace VSPackages do sady Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) , které obsahuje část o aktualizaci rozšiřujících projektů na balíčky NuGet.

## <a name="light-bulbs"></a>Žárovky
 Jedním z nejzajímavějších nových způsobů psaní kódu rozšíření je poskytnout projekt Roslyn. Další informace najdete v tématu [Roslyn](https://github.com/dotnet/Roslyn).

 Žárovky představují novou funkci, která se dodává s VSSDK. Jsou to ikony používané v editoru sady Visual Studio, které se rozbalí k zobrazení sady akcí refaktoringu kódu nebo oprav pro problémy identifikované vestavěnými analyzátory kódu. Další informace najdete v tématu [Návod: zobrazení návrhů](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)žárovky.

## <a name="updated-user-experience-guidelines"></a>Aktualizované pokyny pro činnost koncového uživatele
 Navrhujete nová rozšíření nebo funkce pro Visual Studio? Podívejte se na aktualizované a rozšířené [pokyny pro uživatelské prostředí sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Najdete [tokeny barev](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [velikosti písem](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specifikace rozložení dialogů](../extensibility/ux-guidelines/layout-for-visual-studio.md)a další pokyny, které potřebujete k bezproblémové integraci nového uživatelského rozhraní se sadou Visual Studio.
