---
title: Rozšíření aplikace Visual Studio pro odesílání | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700113"
---
# <a name="shipping-visual-studio-extensions"></a>Odesílání rozšíření sady Visual Studio
Po dokončení vývoje rozšíření ho můžete nainstalovat na jiné počítače, sdílet je s přáteli a spolupracovníky nebo publikovat na webu Visual Studio Marketplace. V této části vysvětlujeme všechny věci, které musíte udělat, abyste mohli publikovat a udržovat rozšíření: práce se soubory .vsix, publikování, lokalizace a aktualizace.

## <a name="working-with-vsix-extensions"></a>Práce s rozšířeními VSIX
 Rozšíření VSIX můžete vytvořit vytvořením prázdného projektu VSIX a následným přidáním různých šablon položek. Další informace naleznete [v tématu Šablona projektu VSIX](../extensibility/vsix-project-template.md).

 Formát VSIX můžete použít k balení šablon projektů, šablon položek, komponent VSPackages, Managed Extensibility Framework (MEF), ovládacích prvků **panelu nástrojů,** sestavení a vlastních typů (to zahrnuje vlastní úvodní stránky pro Visual Studio 2017). Formát VSIX používá nasazení založené na souborech. Další informace o balíčcích VSIX naleznete [v tématu Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Formát VSIX nepodporuje instalaci fragmentů kódu. Nepodporuje také některé další scénáře, jako je například zápis do globální mezipaměti sestavení (GAC) nebo do systémového registru. Pokud potřebujete zapisovat do gac nebo registru v instalaci, musíte použít Instalační službu systému Windows. Další informace naleznete [v tématu Příprava rozšíření pro nasazení Instalační služby systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publikování rozšíření na tržišti Sady Visual Studio
 Rozšíření můžete distribuovat jiným osobám jednoduše tak, že jim pošlete soubor .vsix nebo vložíte na server. Ale nejlepší způsob, jak dostat svůj kód do rukou mnoha lidí, je dát ji na [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozšíření Visual Studio Marketplace jsou k dispozici uživatelům sady Visual Studio prostřednictvím **rozšíření a aktualizace**. Další informace naleznete v [tématu Hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Úplný příklad, který ukazuje, jak nahrát rozšíření na tržiště Sady Visual Studio, najdete v [tématu Návod: Publikování rozšíření sady Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Privátní galerie
 Při vývoji ovládacích prvků, šablon a nástrojů je můžete sdílet s vaší organizací tak, že je zveřejníte v soukromé galerii v síti intranet. Další informace naleznete [v tématu Soukromé galerie](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalizace rozšíření
 Pokud plánujete uvolnit rozšíření v různých národních prostředích, měli byste zvážit jeho lokalizaci. Vysvětlení toho, co se týká, naleznete v [tématu Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualizace a správa verzí rozšíření
 Po publikování rozšíření přijde čas, kdy je třeba jej aktualizovat. Informace o tom, jak aktualizovat rozšíření, které bylo publikováno na webu Visual Studio Marketplace, najdete v [tématu Jak aktualizovat rozšíření](../extensibility/how-to-update-a-visual-studio-extension.md).

 Rozšíření můžete nastavit tak, aby podporovalo více verzí sady Visual Studio. Další informace naleznete [v tématu Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Vysvětluje, jak použít šablonu projektu VSIX k instalaci vlastní šablony projektu.|
|[Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Popisuje součásti balíčku VSIX.|
|[Šablona projektu VSIX](../extensibility/vsix-project-template.md)|Obsahuje podrobné pokyny o tom, jak zabalit a publikovat rozšíření.|
|[Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md)|Vysvětluje, jak poskytnout lokalizovaný text pro proces instalace pomocí souborů extension.vsixlangpack.|
|[Postupy: Aktualizace rozšíření](../extensibility/how-to-update-a-visual-studio-extension.md)|Popisuje, jak aktualizovat rozšíření v systému a jak nasadit aktualizaci do existující rozšíření sady Visual Studio.|
|[Postupy: Přidání závislosti k balíčku VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Popisuje, jak přidat odkazy na balíčky nasazení VSIX.|
|[Příprava rozšíření pro nasazení Instalační služby systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Vysvětluje, jak nasadit rozšíření pomocí Instalační služby systému Windows.|
|[Podepisování balíčků VSIX](../extensibility/signing-vsix-packages.md)|Vysvětluje, jak podepsat balíčky VSIX.|
|[Privátní galerie](../extensibility/private-galleries.md)|Vysvětluje, jak vytvořit soukromé galerie pro rozšíření.|
|[Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Ukazuje, jak mít rozšíření podporu více verzí sady Visual Studio.|
|[Vyhledání sady Visual Studio](locating-visual-studio.md)|Popisuje, jak najít instance sady Visual Studio pro vlastní nasazení rozšíření.|
