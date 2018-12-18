---
title: Začínáme s vývojem rozšíření | Dokumentace Microsoftu
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
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85813c32ec8c4be3e120bbb3a67922379233878c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056562"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Začínáme s vývojem rozšíření sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud jste nikdy napsali před rozšíření sady Visual Studio, pravděpodobně máte nějaké dotazy. Uvádíme některé z nejběžnějších ty. Pokud nevidíte informace, které hledáte, použijte tlačítko zpětnou vazbu (**byla tato stránka užitečná?** v dolní části obrazovky) požádat o co chcete.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Jaký software potřebujete pro vývoj rozšíření sady Visual Studio?
 Je potřeba nainstalovat sadu Visual Studio 2015 SDK kromě sady Visual Studio 2015 pro vývoj rozšíření sady Visual Studio.   Visual Studio 2015 SDK můžete nainstalovat jako součást pravidelných instalace nebo ji můžete nainstalovat později. Další informace o instalaci sady Visual Studio SDK naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Jaké druhy věcí můžete dělat s rozšířeními Visual Studia?
 Pouze nebe při rozhodování o užívat různých rozšíření sady Visual Studio. Samozřejmě většina rozšíření mají něco, co můžete dělat s psaním kódu, ale, která nemusí být případ. Tady je několik příkladů typů rozšíření, která můžete vytvořit:

- Podpora jazyků, které nejsou zahrnuty v sadě Visual Studio s barevné zvýrazňování syntaxe, IntelliSense a podporu kompilátoru a ladění

- Nástroje pro produktivitu, které rozšiřují základní integrované vývojové prostředí vyzkoušejte další šablony, dialogová okna refaktoringu, nový kód nebo okna nástrojů

- Ať už specifický pro doménu pro scénáře, jako je podpora návrhu nebo cloudových dat

  Příklady rozšíření, podívejte se [Galerie sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/). Můžete taky využít podívat [Visual Studio otevřete zdrojový rozšíření](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).

## <a name="which-visual-studio-features-can-i-extend"></a>Které funkce Visual Studia můžete rozšířit?
 Teoreticky vzato můžete rozšířit téměř libovolnou část aplikace Visual Studio: nabídky, panely nástrojů, příkazy, windows, řešení, projekty, editory a tak dále.

 V praxi jsme našli, funkce, které většinu lidí by rádi rozšířili jsou příkazy, nabídky a panely nástrojů, windows, technologie IntelliSense a projekty. Tady jsou odkazy na relevantní části:

-   [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md): Přidat vlastní položky do sady Visual Studio nabídek a panelů nástrojů. Můžete využít k otevření nové funkce sady Visual Studio nebo vlastních aplikací externí pomocné rutiny. Můžete také zadat vlastní klávesové zkratky pro vaše položky nabídky.

-   [Rozšíření a přizpůsobení nástrojů Windows](../extensibility/extending-and-customizing-tool-windows.md): rozšíření existujícími okny nástrojů nebo vytvořit vlastní panel nástrojů. Například můžete přidat nové vlastnosti **vlastnosti**, nebo můžete vytvořit nového okna nástroje pro přidání dalších funkcí.

-   [Editor a rozšíření služeb jazyka](../extensibility/editor-and-language-service-extensions.md): Přidat vlastní přizpůsobení informace IntelliSense poskytované pro jazyky Visual Studio, nebo vytvoří podpora pro nový programovací jazyky. Můžete vytvořit nový příkaz dokončování, nabízení návrhů a nové popisky rychlé informace. Pomocí žárovek můžete přidat refaktoringu návrhy a opravy kódu pro podporu nové programovací jazyky.

-   [Rozšíření projektů](../extensibility/extending-projects.md)

-   [Rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md)

-   [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)

-   [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

-   [Izolované prostředí sady Visual Studio](../extensibility/visual-studio-isolated-shell.md)

##  <a name="BKMK_ProjectTemplate"></a> Jaké šablony projektu jsou poskytovány VSSDK?
 Dva hlavní typy rozšíření jsou rozšíření VSPackages a rozhraní MEF. Rozšíření VSPackage se obecně používají pro rozšíření, které používají nebo rozšířit příkazů, nástrojů oken a projekty. Rozšíření rozhraní MEF umožňují rozšířit nebo upravit editoru sady Visual Studio.

 Pro rozšíření jazyka Visual C# a Visual Basic poskytuje VSSDK prázdná šablona projektu VSIX, které můžete použít společně s nové šablony položky, které vytvářejí, příkazy nabídky, panely nástrojů a rozšíření editoru. Další informace najdete v tématu [co je nového ve službě Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). Můžete také pomocí této šablony balíček šablony projektů, fragmenty kódu a další artefakty pro distribuci ostatním uživatelům.

 Pro jazyk C++ průvodce VSPackage poskytuje kód pro přidání příkazů nabídky, panely nástrojů a vlastních editorech.

 Šablona izolovaného prostředí slouží k rozšíření v prostředí nástroje Visual Studio, kterou můžete značku a distribuovat jako vlastní verzi balíčku. Následující témata ukazují, jak začít pracovat s jednotlivými typy rozšíření:

-   Příkazy nabídky: [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)

-   Nástroje systému windows: [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md)

-   Rozšíření editoru: [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   Základní rozšíření VSPackages: [vytváření rozšíření pomocí VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

-   Šablona projektu VSIX: [Začínáme s šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

-   Izolované prostředí sady Visual Studio: [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Jak získám mého rozšíření, aby vypadala jako Visual Studio?
 Skvělé tipy k návrhu uživatelského rozhraní pro rozšíření v [Visual Studio zkušenosti uživatelů](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Kde najdu příklady VSSDK kódu?
 Jednotlivé odkazy uvedené v předchozí části jste podrobné návody, které ukazují, jak implementovat konkrétní funkce. Můžete také vyhledat opensourcová VSSDK ukázky na Githubu v [ukázky sady Visual Studio](https://aka.ms/vs2015sdksamples).

## <a name="how-can-i-distribute-my-extension"></a>Jak je můžete distribuovat mého rozšíření?
 Můžete nainstalovat rozšíření na jiném počítači nebo odeslat do vašich přátel jako soubor .vsix, který nainstalujete poklepáním. Můžete najít další informace o balíčků VSIX v [přesouvání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Můžete také publikovat vaše rozšíření v Galerii Visual Studio, díky tomu je viditelná pro velký počet zákazníků sady Visual Studio. Příklad vytvoření balíčku rozšíření pro galerii najdete v tématu [názorný postup: publikování rozšíření sady Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Další informace o tom, co potřebujete udělat, aby publikovat v galerii najdete v tématu [produkty a rozšíření pro Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
