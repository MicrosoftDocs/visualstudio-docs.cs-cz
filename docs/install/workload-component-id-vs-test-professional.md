---
title: Visual Studio Test Professional úlohy a ID komponent
titleSuffix: ''
description: Pomocí ID pracovního vytížení a komponenta Visual Studio poskytuje integrované testovací nástroje pro všeobecně testery
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 09/23/2019
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
ms.openlocfilehash: d61105a16919e8384aad961d62a81ff3a8688b25
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213648"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Professional adresář součástí

Tabulky v tomto seznamu stránce ID, můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo je můžete zadat jako závislost v manifestu VSIX. Všimněte si, že přidáme další součásti vydaných aktualizací sady Visual Studio.

Všimněte si také následující stránka:

* Každá úloha má vlastní oddíl, za nímž následuje Identifikátor pracovního vytížení a tabulku komponent, které jsou k dispozici pro pracovní vytížení.
* Ve výchozím nastavení **vyžaduje** součásti nainstaluje, když jste si nainstalovali úlohu.
* Pokud budete chtít, můžete nainstalovat také **doporučená** a **volitelné** komponenty.
* Přidali jsme také oddíl, který obsahuje další součásti, které nejsou pod něj nespadá u jakékoli úlohy.

Když nastavíte závislosti v manifestu VSIX, je nutné zadat ID součástí pouze. Určení závislostí naše minimální součástí pomocí tabulek na této stránce. V některých případech to může znamenat, že zadáváte pouze jednu komponentu z pracovního vytížení. V jiných scénářích může znamenat, že zadáte více komponent z jedné úlohy nebo více komponent z více úloh. Další informace najdete v [tématu Postupy: Migrujte projekty rozšiřitelnosti na stránku](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) sady Visual Studio 2017.

Další informace o tom, jak pomocí těchto identifikátorů najdete v části [pomocí parametrů příkazového řádku instalace sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) stránky. A seznam pracovního vytížení a komponenta ID pro ostatní produkty, naleznete v tématu [funkcí sady Visual Studio 2017 a ID součástí](workload-and-component-ids.md) stránky.

## <a name="test-professional"></a>Test Professional

**ÚČET** Microsoft.VisualStudio.Workload.TestProfessional

**Popis:** Test Professional poskytuje integrované testovací nástroje zaměřené na obecné testery, které jim pomůžou zajistit jejich požadavky na testování napříč celým životním cyklem testování.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | Požadováno

## <a name="unaffiliated-components"></a>Nespojená komponenty

Toto jsou komponenty, které nejsou zahrnuty u jakékoli úlohy, ale může vybrat jako jednotlivých komponent.

ID součásti | Název | Version
--- | --- | ---
není k dispozici | není k dispozici | není k dispozici

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
  * [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
