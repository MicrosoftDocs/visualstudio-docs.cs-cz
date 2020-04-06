---
title: Základní informace o integraci správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705239"
---
# <a name="source-control-integration-essentials"></a>Základy integrace správy zdrojového kódu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]podporuje dva typy integrace správy zdrojového kódu: modul plug-in správy zdrojového kódu, který poskytuje základní funkce a je vytvořen pomocí rozhraní Plug-in Source Control Plug-in API (dříve známé jako rozhraní MSSCCI API) a řešení integrace správy zdrojového kódu založené na balíčku, které poskytuje robustnější funkce.

## <a name="source-control-plug-in"></a>Modul plug-in správy zdrojového kódu
 Modul plug-in správy zdrojového kódu je napsán jako dll, který implementuje rozhraní plug-in správy zdrojového kódu. Funkce integrace registrace a správy zdrojového kódu je k dispozici prostřednictvím rozhraní API. Tento přístup je jednodušší implementovat než zdrojového ovládacího [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prvku VSPackage a používá uživatelské rozhraní (UI) pro většinu operací správy zdrojového kódu.

 Chcete-li implementovat modul plug-in správy zdrojového kódu pomocí rozhraní API modulu plug-in správy zdrojového kódu, postupujte takto:

1. Vytvořte dll, která implementuje funkce zadané [v modulech plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md).

2. Zaregistrujte dll provedením příslušných položek registru, jak je popsáno v [části Postup: Instalace modulu plug-in správy zdrojového kódu](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Vytvořte pomocné uzlové ui a zobrazte ho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] po zobrazení pomocí balíčku adaptéru pro řízení zdrojového kódu (součást, která zpracovává funkce správy zdrojového kódu prostřednictvím modulů plug-in správy zdrojového kódu).

   Další informace naleznete [v tématu Creating a Source Control Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Správa zdrojového kódu VSPackage
 Zdroj ovládacího prvku VSPackage implementace umožňuje vyvinout [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vlastní náhradu pro řízení zdrojového kódu. Tento přístup poskytuje úplnou kontrolu nad integrace správy zdrojového kódu, ale vyžaduje, abyste poskytli prvky uživatelského rozhraní a implementovali rozhraní správy zdrojového kódu, která by jinak byla poskytnuta v rámci přístupu modulu plug-in.

 Chcete-li implementovat zdrojového ovládacího prvku VSPackage, musíte:

1. Vytvořte a zaregistrujte vlastní ovládací prvek zdroj VSPackage, jak je popsáno v [registraci a výběru](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Nahraďte výchozí ovládací prvek zdrojového kódu vlastním ui. Viz [Vlastní uživatelské rozhraní](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Určete glyfy, které mají být použity, a zpracovat události glyfů **Průzkumníka řešení.** Viz [Ovládání glyfů](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Zpracovat události úprav dotazu a ukládání dotazů, jak je znázorněno v [seznamu Proukládání dotazů .](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

   Další informace naleznete [v tématu Creating a Source Control VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Viz také
- [Přehled](../../extensibility/internals/source-control-integration-overview.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)
