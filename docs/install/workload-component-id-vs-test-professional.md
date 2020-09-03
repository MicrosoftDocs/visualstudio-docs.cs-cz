---
title: Visual Studio Test Professional úlohy a ID komponent
titleSuffix: ''
description: Použití úloh sady Visual Studio a ID komponent k poskytování integrovaných testovacích nástrojů pro obecné testery
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: 61a52d98f695a6420dd6081117b8c6c4e83ae0a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81276211"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Professional adresář součástí

Tabulky na této stránce uvádějí ID, která můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo které můžete zadat jako závislost v manifestu VSIX. Všimněte si, že přidáme další komponenty jako aktualizace vydané do sady Visual Studio.

Všimněte si také následujících informací o stránce:

* Každá úloha má svůj vlastní oddíl následovaný ID úlohy a tabulkou komponent, které jsou k dispozici pro zatížení.
* Ve výchozím nastavení se **požadované** součásti nainstalují při instalaci úlohy.
* Pokud se rozhodnete, můžete nainstalovat také **Doporučené** a **volitelné** součásti.
* Přidali jsme také část, která obsahuje seznam dalších komponent, které nejsou přidružené k žádnému zatížení.

Při nastavování závislostí v manifestu VSIX je nutné zadat pouze ID součástí. Pomocí tabulek na této stránce můžete určit minimální závislosti součástí. V některých scénářích to může znamenat, že zadáváte jenom jednu komponentu z úlohy. V jiných scénářích to může znamenat, že zadáváte více komponent z jedné úlohy nebo z více komponent z více úloh. Další informace naleznete v tématu [Postupy: migrace projektů rozšíření na stránku sady Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

Další informace o použití těchto identifikátorů najdete v tématu věnovaném [použití parametrů příkazového řádku k instalaci stránky sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) . Seznam úloh a ID komponent pro jiné produkty najdete na stránce [Visual Studio 2017 – úlohy a ID komponent](workload-and-component-ids.md) .

## <a name="test-professional"></a>Test Professional

**ID:** Microsoft. VisualStudio. úlohy. TestProfessional

**Popis:** Test Professional poskytuje integrované testovací nástroje zaměřené na obecné testery, které jim pomůžou zajistit jejich požadavky na testování napříč celým životním cyklem testování.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Název | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. VisualStudio. Component. TestTools. FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. TestTools. MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | Vyžadováno

## <a name="unaffiliated-components"></a>Nepřidružené součásti

Jedná se o součásti, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé komponenty.

ID součásti | Název | Verze
--- | --- | ---
Není k dispozici | Není k dispozici | Není k dispozici

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
  * [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
