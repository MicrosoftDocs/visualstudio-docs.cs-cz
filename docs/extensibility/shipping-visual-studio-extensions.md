---
title: Expedice rozšíření pro Visual Studio | Microsoft Docs
description: Naučte se publikovat a udržovat rozšíření sady Visual Studio SDK, včetně práce se soubory VSIX, publikováním, lokalizací a aktualizací.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c88c80ffbc1e80815b8370a940a75c0eb197ff78
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090132"
---
# <a name="shipping-visual-studio-extensions"></a>Odesílání rozšíření sady Visual Studio
Po dokončení vývoje rozšíření ho můžete nainstalovat na jiné počítače, sdílet ho s přáteli a spolupracovníky nebo ho publikovat na Visual Studio Marketplace. V této části vyvysvětlíme všechny věci, které potřebujete k tomu, abyste mohli publikovat a udržovat vaše rozšíření: práce se soubory VSIX, publikováním, lokalizací a aktualizací.

## <a name="working-with-vsix-extensions"></a>Práce s rozšířeními VSIX
 Rozšíření VSIX můžete vytvořit vytvořením prázdného projektu VSIX a následným přidáním různých šablon položek. Další informace naleznete v tématu [Šablona projektu VSIX](../extensibility/vsix-project-template.md).

 Formát VSIX lze použít k zabalení šablon projektů, šablon položek, sad VSPackage, Managed Extensibility Framework (MEF) komponent, ovládacích prvků **panelu nástrojů** , sestavení a vlastních typů (to zahrnuje vlastní úvodní stránky pro sadu Visual Studio 2017). Formát VSIX používá nasazení na základě souborů. Další informace o balíčcích VSIX naleznete v tématu [anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Formát VSIX nepodporuje instalaci fragmentů kódu. Nepodporuje také některé jiné scénáře, jako je například zápis do globální mezipaměti sestavení (GAC) nebo do systémového registru. Pokud potřebujete zapisovat do globální mezipaměti sestavení (GAC) nebo do registru v instalaci, je nutné použít Instalační služba systému Windows. Další informace najdete v tématu [Příprava rozšíření pro nasazení Instalační služba systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publikování rozšíření na Visual Studio Marketplace
 Rozšíření můžete ostatním lidem distribuovat jednoduše jejich odesláním do souboru. VSIX nebo vložením na server. Nejlepším způsobem, jak získat kód v rukou velké části lidí, je umístit ho do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Pro uživatele sady Visual Studio jsou k dispozici rozšíření Visual Studio Marketplace prostřednictvím **rozšíření a aktualizací**. Další informace najdete v tématu [vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Úplný příklad, který ukazuje, jak nahrát rozšíření Visual Studio Marketplace, najdete v tématu [Návod: publikování rozšíření aplikace Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Privátní galerie
 Když vyvíjíte ovládací prvky, šablony a nástroje, můžete je sdílet s vaší organizací, a to jejich publikováním do soukromé galerie v intranetu. Další informace najdete v tématu [soukromé Galerie](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalizace rozšíření
 Pokud máte v úmyslu uvolnit rozšíření v různých národních prostředích, měli byste zvážit jeho lokalizaci. Vysvětlení toho, co se týká, najdete v tématu [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualizace a správa verzí rozšíření
 Po publikování rozšíření bude k dispozici čas potřebný k jeho aktualizaci. Chcete-li zjistit, jak aktualizovat rozšíření, které bylo Publikováno v Visual Studio Marketplace, přečtěte si téma [Postup: aktualizace rozšíření](../extensibility/how-to-update-a-visual-studio-extension.md).

 Rozšíření můžete nastavit tak, aby podporovalo více verzí sady Visual Studio. Další informace najdete v tématu [Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Vysvětluje, jak použít šablonu projektu VSIX k instalaci vlastní šablony projektu.|
|[Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Popisuje součásti balíčku VSIX.|
|[Šablona projektu VSIX](../extensibility/vsix-project-template.md)|Poskytuje podrobné pokyny pro zabalení a publikování rozšíření.|
|[Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md)|Vysvětluje, jak poskytnout lokalizovaný text pro instalační proces pomocí souborů s příponou. vsixlangpack.|
|[Postupy: Aktualizace rozšíření](../extensibility/how-to-update-a-visual-studio-extension.md)|Popisuje, jak aktualizovat rozšíření v systému a jak nasadit aktualizaci do stávajícího rozšíření sady Visual Studio.|
|[Postupy: Přidání závislosti k balíčku VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Popisuje, jak přidat odkazy na balíčky nasazení VSIX.|
|[Příprava rozšíření pro nasazení Instalační služby systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Vysvětluje, jak nasadit rozšíření pomocí Instalační služba systému Windows.|
|[Podepisování balíčků VSIX](../extensibility/signing-vsix-packages.md)|Vysvětluje, jak podepisovat balíčky VSIX.|
|[Soukromé galerie](../extensibility/private-galleries.md)|Vysvětluje, jak vytvořit privátní Galerie pro rozšíření.|
|[Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Ukazuje, jak vaše rozšíření podporuje více verzí sady Visual Studio.|
|[Vyhledání sady Visual Studio](locating-visual-studio.md)|Popisuje, jak vyhledat instance sady Visual Studio pro nasazení vlastního rozšíření.|
