---
title: Prvky modelu projektu | Microsoft Docs
description: Přečtěte si o prvcích modelu projektu a o tom, jak se rozhraní a implementace všech projektů v aplikaci Visual Studio sdílí se základní strukturou.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 85b31996a7a0636f136e43531e69fe25c6d87d8f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061287"
---
# <a name="elements-of-a-project-model"></a>Prvky modelu projektu
Rozhraní a implementace všech projektů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rámci sdílí základní strukturu: projektový model pro typ projektu. V modelu projektu, který je VSPackage, který vyvíjíte, vytváříte objekty, které vyhovují vašim rozhodnutím o návrhu a pracují společně s globálními funkcemi poskytovanými IDE. I když máte kontrolu nad tím, jak je položka projektu trvalá, například neřídíte oznámení, že soubor musí být trvalý. Když uživatel umístí fokus na otevřenou položku projektu a klikne na tlačítko **Uložit** v nabídce **soubor** na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] řádku nabídek, kód typu projektu musí zachytit příkaz z integrovaného vývojového prostředí, zachovat soubor a odeslat oznámení zpět do integrovaného vývojového prostředí, že soubor již není změněn.

 Vaše VSPackage komunikuje s IDE prostřednictvím služeb, které poskytují přístup k rozhraním IDE. Například přes konkrétní služby můžete monitorovat a směrovat příkazy a poskytnout kontextové informace pro výběry provedené v projektu. Všechny globální funkce IDE, které jsou potřebné pro VSPackage, jsou poskytovány službami. Další informace o službách najdete v tématu [How to: get a Service](../../extensibility/how-to-get-a-service.md).

 Další pokyny k implementaci:

- Jeden model projektu může obsahovat více než jeden typ projektu.

- Typy projektů a propracované továrny projektu jsou registrovány nezávisle s identifikátory GUID.

- Každý projekt musí mít soubor šablony nebo průvodce pro inicializaci nového souboru projektu, když uživatel vytvoří nový projekt prostřednictvím [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní. Například [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] šablony inicializují, co nakonec se stanou soubory. vcproj.

  Následující ilustrace znázorňuje primární rozhraní, služby a objekty, které tvoří typickou implementaci projektu. `HierUtil7`K vytvoření základních objektů a dalšího programovacího často používaného programování můžete použít pomocníka aplikace. Další informace o `HierUtil7` Pomocníkovi aplikace naleznete v tématu [použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](/previous-versions/bb166212(v=vs.100)).

  ![Obrázek modelu projektu sady Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Model projektu

  Další informace o rozhraních a službách uvedených v předchozím diagramu a dalších volitelných rozhraních, která nejsou součástí diagramu, najdete v tématu [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md).

  Projekty mohou podporovat příkazy, a proto musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní pro účast v směrování příkazů prostřednictvím identifikátorů GUID kontextu příkazu.

## <a name="see-also"></a>Viz také
- [Kontrolní seznam: vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](/previous-versions/bb166212(v=vs.100))
- [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Vytváření instancí projektu pomocí továrnování projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Postupy: získání služby](../../extensibility/how-to-get-a-service.md)
- [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)