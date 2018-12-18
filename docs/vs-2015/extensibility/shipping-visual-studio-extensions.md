---
title: Přesouvání rozšíření | Dokumentace Microsoftu
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
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10e2cacb07c4040fb81aa01e8bd629e1ae593f7c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062545"
---
# <a name="shipping-visual-studio-extensions"></a>Odesílání rozšíření sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Poznámka:**: The Galerie sady Visual Studio teď nahrazuje Visual Studio Marketplace. Zobrazte nejnovější verzi tohoto tématu podrobnosti.


Po dokončení vývoje rozšíření, nainstalujte ho na jiné počítače, sdílet s přáteli nebo kolegy nebo ho publikovat v Galerii Visual Studio. V této části vám vysvětlíme, vše, co musíte udělat, aby bylo možné publikovat a spravovat vaše rozšíření: práce se soubory VSIX, publikování, lokalizace a aktualizace.

## <a name="working-with-vsix-extensions"></a>Práce s rozšíření VSIX
 Vytvoření prázdného projektu VSIX a následným přidáním jiná položka šablony do ní můžete vytvořit rozšíření VSIX. Další informace najdete v tématu [šablonou projektu VSIX](../extensibility/vsix-project-template.md).

 Balíček šablony projektů, položku šablony, balíčky VSPackages, součásti Managed Extensibility Framework (MEF), můžete použít formát VSIX **nástrojů** ovládací prvky, sestavení a vlastní typy (to zahrnuje vlastní úvodní stránky). Formát VSIX využívá nasazení založené na souboru. Další informace o balíčcích VSIX, naleznete v tématu [anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Formát VSIX nepodporuje instalaci fragmentů kódu. Také nepodporuje některých dalších scénářů, jako je například zápis do globální mezipaměti sestavení (GAC) nebo do systémového registru. Pokud budete potřebovat k zápisu do mezipaměti GAC nebo registru v instalaci, musíte použít instalační služby systému Windows. Další informace najdete v tématu [Příprava rozšíření pro Windows Installer nasazení](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Publikování rozšíření do Galerie Visual Studio
 Rozšíření ostatním uživatelům můžete distribuovat jednoduše tak, že jejich souboru .vsix poštovní nebo vložení na serveru. Ale nejlepší způsob, jak získat kód dostat do rukou velké množství lidí je umístit jej [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847). Rozšíření Galerie sady Visual Studio jsou k dispozici uživatelům aplikace Visual Studio prostřednictvím **rozšíření a aktualizace**. Další informace najdete v tématu [hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Úplný příklad, který ukazuje, jak nahrát rozšíření do Galerie Visual Studio, naleznete v tématu [názorný postup: publikování rozšíření sady Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Privátní galerie
 Při vývoji ovládací prvky, šablony a nástroje, můžete je sdílet ve vaší organizaci tím, že publikuje do privátní Galerie na vašem intranetu. Další informace najdete v tématu [privátní Galerie](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalizace rozšíření
 Pokud máte v plánu uvolnit rozšíření v různých národních prostředí, měli byste zvážit, je lokalizace. Vysvětlení, co je zahrnuta, najdete v článku [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualizace a správa verzí rozšíření
 Po publikování rozšíření, budou přicházet čas, kdy je potřeba ho aktualizovat. Postup aktualizace rozšíření, která byla publikována na Galerii Visual Studio najdete v tématu [postupy: aktualizace rozšíření](../extensibility/how-to-update-a-visual-studio-extension.md).

 Můžete nastavit rozšíření pro podporu více verzí sady Visual Studio. Další informace najdete v tématu [podporuje více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Vysvětluje, jak nainstalovat vlastní šablonu projektu pomocí šablony projektu VSIX.|
|[Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Popisuje součásti balíčku VSIX.|
|[Šablona projektu VSIX](../extensibility/vsix-project-template.md)|Obsahuje podrobné pokyny o tom, jak zabalit a publikovat rozšíření.|
|[Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md)|Vysvětluje, jak zajistit lokalizovaný text pro proces instalace pomocí extension.vsixlangpack soubory.|
|[Postupy: Aktualizace rozšíření](../extensibility/how-to-update-a-visual-studio-extension.md)|Popisuje postup aktualizace rozšíření ve vašem systému a jak nasadit aktualizace do existujícího rozšíření sady Visual Studio.|
|[Postupy: Přidání závislosti k balíčku VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Popisuje, jak přidat odkazy na balíčky VSIX pro nasazení.|
|[Příprava rozšíření pro nasazení Instalační služby systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Vysvětluje, jak nasazení vašeho rozšíření Instalační služby systému Windows.|
|[Podepisování balíčků VSIX](../extensibility/signing-vsix-packages.md)|Vysvětluje, jak k podepisování balíčků VSIX.|
|[Privátní galerie](../extensibility/private-galleries.md)|Vysvětluje, jak vytvořit privátní Galerie rozšíření.|
|[Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Ukazuje, jak mají vaše rozšíření podpory více verzí sady Visual Studio.|
