---
title: Začínáse vyvíjet rozšíření sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699744"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Začínáme s vývojem rozšíření sady Visual Studio

Pokud jste nikdy předtím nenapsali rozšíření sady Visual Studio, pravděpodobně máte nějaké otázky. Vyjmenovali jsme zde některé z nejběžnějších. Pokud nevidíte informace, které hledáte, použijte tlačítka pro zpětnou vazbu **(Byla tato stránka užitečná?** v dolní části obrazovky) a požádejte o to, co chcete.

> [!NOTE]
> Tento článek se vztahuje na Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Rozšíření Visual Studia pro Mac](/visualstudio/mac/extending-visual-studio-mac). Kód sady Visual Studio najdete v [tématu Rozhraní API rozšíření kódu sady Visual Studio](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Jaký software potřebuji k vývoji rozšíření sady Visual Studio?

Chcete-li vyvíjet rozšíření sady Visual Studio, je třeba nainstalovat sady Visual Studio SDK kromě sady Visual Studio. Sady Visual Studio SDK můžete nainstalovat jako součást pravidelnéinstalace nebo ji můžete nainstalovat později. Další informace o instalaci sady Visual Studio SDK naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Jaké druhy věcí lze dělat s rozšířeními sady Visual Studio?

Nebe je limit, pokud jde o představu různých rozšíření sady Visual Studio. Samozřejmě, většina rozšíření má něco společného s psaním kódu, ale to nemusí být případ. Zde je několik příkladů typů rozšíření, které můžete vytvořit:

- Podpora jazyků, které nejsou zahrnuty v sadě Visual Studio, s barvicí syntaxe, Technologie IntelliSense a podporou kompilátoru a ladění

- Nástroje pro zvýšení produktivity, které rozšiřují základní prostředí IDE o další šablony, refaktoring kódu, nová dialogová okna nebo okna nástrojů

- Návrháři specifických pro doménu pro scénáře, jako je návrh dat nebo cloudová podpora

Příklady rozšíření, podívejte se na [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Mnoho rozšíření jsou open sourced a Marketplace obsahuje odkazy na jejich úložiště GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Které funkce sady Visual Studio lze rozšířit?

Teoreticky můžete rozšířit téměř libovolnou část sady Visual Studio: nabídky, panely nástrojů, příkazy, okna, řešení, projekty, editory a tak dále.

V praxi jsme zjistili, že funkce, které chce většina lidí rozšířit, jsou příkazy, nabídky a panely nástrojů, okna, technologie IntelliSense a projekty. Zde jsou odkazy na příslušné oddíly:

- [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md): přidejte vlastní položky do nabídek a panelů nástrojů sady Visual Studio. Můžete je použít ke spuštění nové funkce sady Visual Studio nebo vlastní externí pomocné aplikace. Můžete také zadat vlastní zkratky pro položky nabídky.

- [Rozšíření a přizpůsobení nástroje Windows](../extensibility/extending-and-customizing-tool-windows.md): rozšířit stávající okna nástrojů nebo vytvořit vlastní nástroj okna. Můžete například přidat nové vlastnosti **vlastnosti nebo**můžete vytvořit nové okno nástroje pro přidání dalších funkcí.

- [Rozšíření editoru a jazykových služeb](../extensibility/editor-and-language-service-extensions.md): přidejte vlastní vlastní vlastní nastavení do technologie IntelliSense poskytované pro jazyky sady Visual Studio nebo vytvořte podporu pro nové programovací jazyky. Můžete vytvořit nové dokončování příkazů, návrhy a nové popisky QuickInfo. Pomocí žárovek můžete přidat návrhy refaktoringu a opravy kódu pro podporu nových programovacích jazyků.

- [Rozšíření projektů](../extensibility/extending-projects.md)

- [Rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md)

- [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)

- [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Izolované prostředí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>Jaké šablony projektů poskytuje sada VSSDK?
 Dva hlavní typy rozšíření jsou Rozšíření VSPackages a MEF. Obecně však Rozšíření VSPackage se používají pro rozšíření, která používají nebo rozšiřují příkazy, okna nástrojů a projekty. Rozšíření MEF se používají k rozšíření nebo přizpůsobení editoru sady Visual Studio.

 Pro rozšíření Visual C# a Visual Basic poskytuje sada VSSDK prázdnou šablonu projektu VSIX, kterou můžete použít společně s novými šablonami položek, které vytvářejí příkazy nabídek, okna nástrojů a rozšíření editoru. Tuto šablonu můžete také použít k balení šablon projektů, fragmentů kódu a dalších artefaktů pro distribuci ostatním uživatelům.

 Pro C++ průvodce VSPackage poskytuje kód pro přidání příkazů nabídky, oken nástrojů a vlastních editorů.

 Šablona Izolované prostředí se používá k balení rozšíření ve verzi prostředí Visual Studio, které můžete označit a distribuovat jako vlastní. Následující témata ukazují, jak začít s jednotlivými druhy rozšíření:

- Příkazy nabídky: [Vytvoření rozšíření pomocí příkazu Nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)

- Okna nástrojů: [Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md)

- Rozšíření editoru: [Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Základní VSPackages: [Vytvoření rozšíření s VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Šablona projektu VSIX: [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Jak získám rozšíření tak, aby vypadalo jako Visual Studio?
 Získejte skvělé tipy pro návrh uživatelského rozhraní pro vaše rozšíření v [pokynech pro uživatelské prostředí sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Kde najdu příklady kódu VSSDK?
 Každý z odkazů uvedených v předchozí části mají podrobné návody, které ukazují, jak implementovat konkrétní funkce. Můžete také najít open source VSSDK ukázky na GitHub u [Visual Studio ukázky](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Jak mohu rozšíření distribuovat?
 Rozšíření můžete nainstalovat do jiného počítače nebo ji odeslat přátelům jako soubor .vsix, který nainstalujete poklepáním. Další informace o balíčcích VSIX najdete v [aplikaci Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 Rozšíření můžete také publikovat na webu Visual Studio Marketplace, což jej zviditelní pro velký počet zákazníků sady Visual Studio. Příklad balení rozšíření na Marketplace najdete v [tématu Návod: Publikování rozšíření sady Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Další informace o tom, co je potřeba udělat pro publikování na webu Marketplace, najdete v [tématu Produkty a rozšíření pro Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Viz také

- [Rozšíření sady Visual Studio pro Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Rozšíření kódu sady Visual Studio](https://code.visualstudio.com/api)
