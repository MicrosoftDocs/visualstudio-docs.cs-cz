---
title: Zahájení vývoje rozšíření sady Visual Studio | Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63fa0db72a01ddf1f6e1003fc27cf6a28128e036
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269120"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Začínáme s vývojem rozšíření sady Visual Studio

Pokud jste ještě nikdy nezapsali rozšíření sady Visual Studio, pravděpodobně máte k dispozici nějaké dotazy. Tady uvádíme některé z nejběžnějších. Pokud nevidíte informace, které hledáte, použijte tlačítka pro zpětnou vazbu (**byla tato stránka užitečná?** v dolní části obrazovky), pokud chcete požádat o to, co chcete.

> [!NOTE]
> Tento článek se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [rozšíření Visual Studio pro Mac](/visualstudio/mac/extending-visual-studio-mac). Visual Studio Code najdete v tématu [rozhraní API pro rozšíření Visual Studio Code](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Jaký software potřebujete pro vývoj rozšíření sady Visual Studio?

Aby bylo možné vyvíjet rozšíření sady Visual Studio, je třeba nainstalovat sadu Visual Studio SDK společně se sadou Visual Studio. Sadu Visual Studio SDK můžete nainstalovat jako součást pravidelného nastavení, nebo ji můžete nainstalovat později. Další informace o instalaci sady Visual Studio SDK naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Jaké druhy věcí můžete dělat s rozšířeními Visual Studia?

Limit nebe, který je v případě, že se přidávají k imaginárním různým rozšířením sady Visual Studio. Většina rozšíření samozřejmě má něco, co dělat s psaním kódu, ale to nemusí být případ. Tady je několik příkladů typů rozšíření, která můžete vytvořit:

- Podpora pro jazyky, které nejsou zahrnuté v aplikaci Visual Studio s barvou syntaxe, IntelliSense a kompilátor a podpora ladění

- Nástroje pro produktivitu, které rozšiřují základní integrované vývojové prostředí vyzkoušejte další šablony, dialogová okna refaktoringu, nový kód nebo okna nástrojů

- Ať už specifický pro doménu pro scénáře, jako je podpora návrhu nebo cloudových dat

Příklady rozšíření najdete v [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Řada rozšíření je open source a Marketplace obsahuje odkazy na své úložiště GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Které funkce Visual Studia můžete rozšířit?

Teoreticky vzato můžete rozšířit téměř libovolnou část aplikace Visual Studio: nabídky, panely nástrojů, příkazy, windows, řešení, projekty, editory a tak dále.

V praxi jsme našli, funkce, které většinu lidí by rádi rozšířili jsou příkazy, nabídky a panely nástrojů, windows, technologie IntelliSense a projekty. Tady jsou odkazy na relevantní části:

- [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md): Přidat vlastní položky do sady Visual Studio nabídek a panelů nástrojů. Můžete využít k otevření nové funkce sady Visual Studio nebo vlastních aplikací externí pomocné rutiny. Můžete také zadat vlastní klávesové zkratky pro vaše položky nabídky.

- [Rozšíření a přizpůsobení nástrojů Windows](../extensibility/extending-and-customizing-tool-windows.md): rozšíření existujícími okny nástrojů nebo vytvořit vlastní panel nástrojů. Například můžete přidat nové vlastnosti **vlastnosti**, nebo můžete vytvořit nového okna nástroje pro přidání dalších funkcí.

- [Rozšíření pro Editor a jazykové služby](../extensibility/editor-and-language-service-extensions.md): přidejte vlastní vlastní nastavení do technologie IntelliSense poskytované pro jazyky sady Visual Studio nebo vytvořte podporu pro nové programovací jazyky. Můžete vytvořit nový příkaz dokončování, nabízení návrhů a nové popisky rychlé informace. Pomocí žárovek můžete přidat refaktoringu návrhy a opravy kódu pro podporu nové programovací jazyky.

- [Rozšíření projektů](../extensibility/extending-projects.md)

- [Rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md)

- [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)

- [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Izolované prostředí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="BKMK_ProjectTemplate"></a> Jaké šablony projektu jsou poskytovány VSSDK?
 Dva hlavní typy rozšíření jsou rozšíření VSPackages a rozhraní MEF. Rozšíření VSPackage se obecně používají pro rozšíření, které používají nebo rozšířit příkazů, nástrojů oken a projekty. Rozšíření rozhraní MEF umožňují rozšířit nebo upravit editoru sady Visual Studio.

 Pro rozšíření jazyka Visual C# a Visual Basic poskytuje VSSDK prázdná šablona projektu VSIX, které můžete použít společně s nové šablony položky, které vytvářejí, příkazy nabídky, panely nástrojů a rozšíření editoru. Můžete také pomocí této šablony balíček šablony projektů, fragmenty kódu a další artefakty pro distribuci ostatním uživatelům.

 Pro jazyk C++ průvodce VSPackage poskytuje kód pro přidání příkazů nabídky, panely nástrojů a vlastních editorech.

 Šablona izolovaného prostředí slouží k rozšíření v prostředí nástroje Visual Studio, kterou můžete značku a distribuovat jako vlastní verzi balíčku. Následující témata ukazují, jak začít pracovat s jednotlivými typy rozšíření:

- Příkazy nabídky: [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)

- Nástroje systému windows: [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md)

- Rozšíření editoru: [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Základní rozšíření VSPackages: [vytváření rozšíření pomocí VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Šablona projektu VSIX: [Začínáme s šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Jak získám mého rozšíření, aby vypadala jako Visual Studio?
 Skvělé tipy k návrhu uživatelského rozhraní pro rozšíření v [Visual Studio zkušenosti uživatelů](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Kde najdu příklady VSSDK kódu?
 Jednotlivé odkazy uvedené v předchozí části jste podrobné návody, které ukazují, jak implementovat konkrétní funkce. Můžete také vyhledat opensourcová VSSDK ukázky na Githubu v [ukázky sady Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Jak je můžete distribuovat mého rozšíření?
 Můžete nainstalovat rozšíření na jiném počítači nebo odeslat do vašich přátel jako soubor .vsix, který nainstalujete poklepáním. Můžete najít další informace o balíčků VSIX v [přesouvání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Rozšíření můžete také publikovat na Visual Studio Marketplace, což jim umožní zobrazit velký počet zákazníků sady Visual Studio. Příklad balení rozšíření na tržišti najdete v tématu [Návod: publikování rozšíření aplikace Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Další informace o tom, co potřebujete udělat k publikování na webu Marketplace, najdete v tématu [produkty a rozšíření pro Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Viz také:

- [Rozšíření sady Visual Studio pro Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Rozšíření Visual Studio Code](https://code.visualstudio.com/api)
