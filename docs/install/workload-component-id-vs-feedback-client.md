---
title: Sady Visual Studio Feedback Client úlohy a ID komponent
titleSuffix: ''
description: Použijte úlohy a ID komponent sady Visual Studio k poskytnutí obsáhlé zpětné vazby pro Azure DevOps Services nebo Team Foundation Server
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 7392a100-100c-458c-9394-828695109015
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: fe4eec389389622f0d87d30edbbd46d7c5b53d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81276302"
---
# <a name="visual-studio-feedback-client-component-directory"></a>Adresář součástí sady Visual Studio Feedback Client

Tabulky na této stránce uvádějí ID, která můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo které můžete zadat jako závislost v manifestu VSIX. Všimněte si, že přidáme další komponenty jako aktualizace vydané do sady Visual Studio.

Všimněte si také následujících informací o stránce:

* Každá úloha má svůj vlastní oddíl následovaný ID úlohy a tabulkou komponent, které jsou k dispozici pro zatížení.
* Ve výchozím nastavení se **požadované** součásti nainstalují při instalaci úlohy.
* Pokud se rozhodnete, můžete nainstalovat také **Doporučené** a **volitelné** součásti.
* Přidali jsme také část, která obsahuje seznam dalších komponent, které nejsou přidružené k žádnému zatížení.

Při nastavování závislostí v manifestu VSIX je nutné zadat pouze ID součástí. Pomocí tabulek na této stránce můžete určit minimální závislosti součástí. V některých scénářích to může znamenat, že zadáváte jenom jednu komponentu z úlohy. V jiných scénářích to může znamenat, že zadáváte více komponent z jedné úlohy nebo z více komponent z více úloh. Další informace naleznete v tématu [Postupy: migrace projektů rozšíření na stránku sady Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

Další informace o použití těchto identifikátorů najdete v tématu věnovaném [použití parametrů příkazového řádku k instalaci stránky sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) . Seznam úloh a ID komponent pro jiné produkty najdete na stránce [Visual Studio 2017 – úlohy a ID komponent](workload-and-component-ids.md) .

## <a name="feedback-client"></a>Feedback Client

**ID:** Microsoft. VisualStudio. úlohy. FeedbackClient

**Popis:** Feedback Client umožňuje účastníkům poskytovat bohatou zpětnou vazbu k Azure DevOps Services nebo Team Foundation Server.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Název | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. VisualStudio. Component. TestTools. FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Vyžadováno

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
