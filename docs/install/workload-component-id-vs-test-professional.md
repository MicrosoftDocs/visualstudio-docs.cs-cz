---
title: Pracovní vytížení visual studio test professional a ID součástí
titleSuffix: ''
description: Použití úloh y Visual Studia a ID součástí k poskytování integrovaných testovacích nástrojů pro generalistické testery
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
ms.openlocfilehash: ececc1815ebc578076d059b00ade1a5fde4552a4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437333"
---
# <a name="visual-studio-test-professional-component-directory"></a>Adresář komponent Visual Studio Test Professional

Tabulky na této stránce uvádějí ID, které můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo které můžete zadat jako závislost v manifestu VSIX. Všimněte si, že budeme přidávat další součásti, jak budeme vydávat aktualizace visual studio.

Všimněte si také následující o stránce:

* Každé pracovní vytížení má vlastní část, následovanou ID pracovního vytížení a tabulkou součástí, které jsou k dispozici pro úlohu.
* Ve výchozím nastavení budou **požadované** součásti nainstalovány při instalaci úlohy.
* Pokud se rozhodnete, můžete také nainstalovat **doporučené** a **volitelné** součásti.
* Přidali jsme také oddíl, který obsahuje seznam dalších součástí, které nejsou přidruženy k žádné pracovní zátěži.

Když nastavíte závislosti v manifestu VSIX, musíte zadat pouze ID součástí. Pomocí tabulek na této stránce určete naše minimální závislosti součástí. V některých případech to může znamenat, že zadáte pouze jednu součást z pracovního vytížení. V jiných scénářích to může znamenat, že zadáte více součástí z jednoho pracovního vytížení nebo více součástí z více úloh. Další informace najdete v tématu [Postup: Migrace projektů rozšiřitelnosti do Visual Studia 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) stránku.

Další informace o použití těchto ID najdete [v tématu Použití parametrů příkazového řádku k instalaci stránky Visual Studia 2017.](use-command-line-parameters-to-install-visual-studio.md) A seznam úloh a ID součástí pro jiné produkty najdete na stránce [Visual Studio 2017 Workload and Component ID.](workload-and-component-ids.md)

## <a name="test-professional"></a>Test Professional

**ID:** Microsoft.VisualStudio.Workload.TestProfessional

**Popis:** Test Professional poskytuje integrované testovací nástroje zaměřené na generalistické testery, které jim pomáhají řídit jejich testovací potřeby v průběhu celého životního cyklu testování.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | Požaduje se

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
