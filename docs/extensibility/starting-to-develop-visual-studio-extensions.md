---
title: Zahájení vývoje rozšíření sady Visual Studio | Microsoft Docs
description: Seznamte se s některými běžnými otázkami, které můžete mít při prvním spuštění napsání rozšíření sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c45ff8b0fd2328a6398f844dc1416decc0ea591
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848081"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Začínáme s vývojem rozšíření sady Visual Studio

Pokud jste ještě nikdy nezapsali rozšíření sady Visual Studio, pravděpodobně máte k dispozici nějaké dotazy. Tady uvádíme některé z nejběžnějších. Pokud nevidíte informace, které hledáte, použijte tlačítka pro zpětnou vazbu (**Tato stránka je užitečná** v pravém horním rohu obrazovky) a zeptejte se na to, co chcete.

> [!NOTE]
> Tento článek se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [rozšíření Visual Studio pro Mac](/visualstudio/mac/extending-visual-studio-mac). Visual Studio Code najdete v tématu [rozhraní API pro rozšíření Visual Studio Code](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Jaký software potřebuji k vývoji rozšíření sady Visual Studio?

Aby bylo možné vyvíjet rozšíření sady Visual Studio, je třeba nainstalovat sadu Visual Studio SDK společně se sadou Visual Studio. Sadu Visual Studio SDK můžete nainstalovat jako součást pravidelného nastavení, nebo ji můžete nainstalovat později. Další informace o instalaci sady Visual Studio SDK najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Jaké druhy věcí lze dělat s rozšířeními sady Visual Studio?

Limit nebe, který je v případě, že se přidávají k imaginárním různým rozšířením sady Visual Studio. Většina rozšíření samozřejmě má něco, co dělat s psaním kódu, ale to nemusí být případ. Tady je několik příkladů typů rozšíření, která můžete sestavit:

- Podpora pro jazyky, které nejsou zahrnuté v aplikaci Visual Studio s barvou syntaxe, IntelliSense a kompilátor a podpora ladění

- Nástroje pro zvýšení produktivity, které šíří základní prostředí IDE pomocí dalších šablon, refaktoringu kódu, nových dialogů nebo oken nástrojů

- Návrháři specifické pro doménu pro scénáře, jako je například návrh dat nebo podpora cloudu

Příklady rozšíření najdete v [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Řada rozšíření je open source a Marketplace obsahuje odkazy na své úložiště GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Které funkce sady Visual Studio můžu roztáhnout?

Teoreticky můžete roztáhnout jenom součást sady Visual Studio: nabídky, panely nástrojů, příkazy, okna, řešení, projekty, editory a tak dále.

V praxi jsme zjistili, že funkce, které většina lidí chce rozšířil, jsou příkazy, nabídky a panely nástrojů, Windows, IntelliSense a projekty. Tady jsou odkazy na relevantní oddíly:

- [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md): Přidání vlastních položek do nabídek a panelů nástrojů sady Visual Studio. Můžete je použít ke spuštění nových funkcí sady Visual Studio nebo vašich externích pomocných aplikací. Můžete také zadat vlastní zkratky pro položky nabídky.

- [Rozšíření a přizpůsobení oken nástrojů](../extensibility/extending-and-customizing-tool-windows.md): rozšíření existujících oken nástrojů nebo vytvoření vlastních oken nástrojů. Můžete například přidat nové vlastnosti do **vlastností**, nebo můžete vytvořit nové okno nástroje pro přidání dalších funkcí.

- [Rozšíření pro Editor a jazykové služby](../extensibility/editor-and-language-service-extensions.md): přidejte vlastní vlastní nastavení do technologie IntelliSense poskytované pro jazyky sady Visual Studio nebo vytvořte podporu pro nové programovací jazyky. Můžete vytvořit nová doplňování příkazů, návrhy a nové popisy QuickInfo. V případě žárovek můžete přidat návrhy refaktoringu a opravy kódu pro podporu nových programovacích jazyků.

- [Rozšíření projektů](../extensibility/extending-projects.md)

- [Rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md)

- [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)

- [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Izolované prostředí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> Jaké šablony projektu poskytuje VSSDK?
 Dva hlavní typy rozšíření jsou VSPackage a rozšíření MEF. Obecně jsou rozšíření VSPackage používána pro rozšíření, která používají nebo rozšiřuje příkazy, okna nástrojů a projekty. Rozšíření MEF slouží k rozšíření nebo přizpůsobení editoru sady Visual Studio.

 Pro rozšíření Visual C# a Visual Basic poskytuje VSSDK prázdnou šablonu projektu VSIX, kterou lze použít společně s šablonami nových položek, které vytvářejí příkazy nabídky, okna nástrojů a rozšíření editoru. Tuto šablonu lze také použít k zabalení šablon projektů, fragmentů kódu a dalších artefaktů pro distribuci jiným uživatelům.

 V jazyce C++ průvodce VSPackage poskytuje kód pro přidání příkazů nabídky, oken nástrojů a vlastních editorů.

 Šablona izolovaného prostředí slouží k zabalení rozšíření ve verzi prostředí sady Visual Studio, které můžete označit a distribuovat jako své vlastní. Následující témata ukazují, jak začít s každým druhem rozšíření:

- Příkazy nabídky: [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)

- Okna nástrojů: [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md)

- Rozšíření editoru: [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Základní sady VSPackage: [vytváření rozšíření pomocí sady VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Šablona projektu VSIX: [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Návody získat rozšíření, aby vypadalo jako Visual Studio?
 V [pokynech pro uživatelské prostředí sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)získáte Skvělé tipy pro návrh uživatelského rozhraní pro vaše rozšíření.

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Kde najdu příklady kódu VSSDK?
 Každý z odkazů uvedených v předchozí části obsahuje podrobné návody, které ukazují, jak implementovat konkrétní funkce. V [ukázkách sady Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples)můžete také najít příklady Open Source VSSDK Samples na GitHubu.

## <a name="how-can-i-distribute-my-extension"></a>Jak můžu distribuovat rozšíření?
 Rozšíření můžete nainstalovat na jiný počítač nebo ho poslat přátelům jako soubor. vsix, který nainstalujete tak, že na něj dvakrát kliknete. Další informace o balíčcích VSIX najdete v [rozšířeních sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Rozšíření můžete také publikovat na Visual Studio Marketplace, což jim umožní zobrazit velký počet zákazníků sady Visual Studio. Příklad balení rozšíření na tržišti najdete v tématu [Návod: publikování rozšíření aplikace Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Další informace o tom, co potřebujete udělat k publikování na webu Marketplace, najdete v tématu [produkty a rozšíření pro Visual Studio](/azure/devops/extend/overview?view=vsts&preserve-view=true).

## <a name="see-also"></a>Viz také

- [Rozšíření sady Visual Studio pro Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Rozšíření Visual Studio Code](https://code.visualstudio.com/api)