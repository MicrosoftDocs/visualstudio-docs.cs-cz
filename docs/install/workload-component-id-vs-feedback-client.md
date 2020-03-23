---
title: Úlohy klienta Visual Studio Feedback a ID komponent
titleSuffix: ''
description: Použití úloh a ID komponent sady Visual Studio k poskytování bohaté zpětné vazby pro služby Azure DevOps Services nebo Team Foundation Server
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
ms.openlocfilehash: 5cba73bd7ea3e0251174ea7a702cd80509fbd954
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113842"
---
# <a name="visual-studio-feedback-client-component-directory"></a>Adresář komponent y Visual Studio Feedback Client

Tabulky na této stránce uvádějí ID, které můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo které můžete zadat jako závislost v manifestu VSIX. Všimněte si, že budeme přidávat další součásti, jak budeme vydávat aktualizace visual studio.

Všimněte si také následující o stránce:

* Každé pracovní vytížení má vlastní část, následovanou ID pracovního vytížení a tabulkou součástí, které jsou k dispozici pro úlohu.
* Ve výchozím nastavení budou **požadované** součásti nainstalovány při instalaci úlohy.
* Pokud se rozhodnete, můžete také nainstalovat **doporučené** a **volitelné** součásti.
* Přidali jsme také oddíl, který obsahuje seznam dalších součástí, které nejsou přidruženy k žádné pracovní zátěži.

Když nastavíte závislosti v manifestu VSIX, musíte zadat pouze ID součástí. Pomocí tabulek na této stránce určete naše minimální závislosti součástí. V některých případech to může znamenat, že zadáte pouze jednu součást z pracovního vytížení. V jiných scénářích to může znamenat, že zadáte více součástí z jednoho pracovního vytížení nebo více součástí z více úloh. Další informace najdete v tématu [Postup: Migrace projektů rozšiřitelnosti do Visual Studia 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) stránku.

Další informace o použití těchto ID najdete [v tématu Použití parametrů příkazového řádku k instalaci stránky Visual Studia 2017.](use-command-line-parameters-to-install-visual-studio.md) A seznam úloh a ID součástí pro jiné produkty najdete na stránce [Visual Studio 2017 Workload and Component ID.](workload-and-component-ids.md)

## <a name="feedback-client"></a>Feedback Client

**ID:** Microsoft.VisualStudio.Workload.FeedbackClient

**Popis:** Klient zpětné vazby umožňuje zúčastněným stranám poskytovat bohatou zpětnou vazbu pro služby Azure DevOps Services nebo Team Foundation Server.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Požaduje se

## <a name="unaffiliated-components"></a>Nepřidružené součásti

Jedná se o součásti, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé součásti.

ID součásti | Name (Název) | Version
--- | --- | ---
neuvedeno | neuvedeno | neuvedeno

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Průvodce správcem sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
  * [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
