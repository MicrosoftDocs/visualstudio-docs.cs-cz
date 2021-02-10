---
title: Vzorce interakce pro Visual Studio | Microsoft Docs
description: Přečtěte si o knihovně běžných vzorů interakce, které můžete použít při vytváření nových funkcí pro sadu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13d111ea6e812de8290433c416a12dbd252662b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942877"
---
# <a name="interaction-patterns-for-visual-studio"></a>Vzory interakcí pro Visual Studio
## <a name="overview"></a>Přehled
 Vzor návrhu je obecně základem návrhu, který lze použít v určitých situacích k řešení problémů s podobnými sadami omezení. Návrháři funkcí a systému tyto vzory návrhu používají jako počáteční body, které je pak možné přizpůsobit na jejich konkrétní situaci.

 Visual Studio má knihovnu běžných vzorů interakce, které byste měli vzít v úvahu při sestavování nových funkcí. Existují dva kontexty Core pro naše vzory návrhu: klient sady Visual Studio (devenv) a GitHub Codespaces (dřív Visual Studio Online). Pro některé problémy s návrhem je všudypřítomný vzor, který funguje dobře ve všech situacích. V mnoha případech se však řešení může lišit pro uživatelské rozhraní, které je prezentováno v prohlížeči a které je hostováno v klientské aplikaci.

### <a name="visual-studio-client-pattern-types"></a>Typy vzorů klientů sady Visual Studio

|Typ vzorku|Description|Příklady|
|------------------|-----------------|--------------|
|**Vzory na úrovni aplikace**|Vzor vysoké úrovně společné pro aplikaci, určení nebo zobrazení kontextu aplikace a obsahující složené a řídicí vzory v nich|– Okna nástrojů<br />– Dokumentová okna|
|**Složené vzory**|Běžné vzory, které mohou být rozloženy napříč vzorci aplikace, nebo rozpoznaný vzor vytvořený několika ovládacími prvky v odlišné konfiguraci|– Zobrazení přepínání<br />– Seznam tvůrců<br />-Zobrazení dat<br />– Oznámení<br />– Ověření<br />-Výběr modelů|
|**Vzory ovládacích prvků**|Konkrétní informace o tom, jak se očekává, že se ovládací prvky nízké úrovně chovají|– Stromová zobrazení<br />-Úpravy v rámci ovládacího prvku mřížky|

## <a name="application-patterns"></a>Vzory aplikací
 V rámci vysoké úrovně obsahuje rozhraní sady Visual Studio několik oken, dialogových oken, příkazů a panelů nástrojů v rámci jednoho integrovaného vývojového prostředí (IDE). Hierarchie sady Visual Studio určuje nabídky kontextu a jednotky. Klíčovým bodem integrace v uživatelském rozhraní rozhraní IDE jsou okna dokumentu, okna nástrojů, projekty, struktura příkazů, textový editor, sada nástrojů, okno Vlastnosti a nástroje > možnosti.

 Existují základní vzory použití pro každý klíč integračních bodů v uživatelském rozhraní rozhraní IDE:

- [Nabídky a příkazy pro Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Vzory aplikací pro Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interakce oken](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Okna nástrojů](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Konvence editoru dokumentů](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialogy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Běžné vzory ovládacích prvků
 Vzory ovládacích prvků jsou převážně o tom, jak se očekává, že se jednotlivé ovládací prvky chovají. Jedná se o jednu oblast, ve které je konzistence nejdůležitější.

 Nejběžnější ovládací prvky v aplikaci Visual Studio by měly postupovat podle pokynů pro stolní počítače s Windows. Naše pokyny obsahují jenom oblasti, ve kterých musíme rozšířit společné konvence s využitím interakcí se sadou Visual Studio, nebo míst, kde jsme zcela nahradili pokyny, aby bylo možné přizpůsobit sadu Visual Studio tak, aby splňovala potřeby našich propracovaných uživatelů.

- [Vzory běžných ovládacích prvků pro Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Běžné ovládací prvky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Textové ovládací prvky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Tlačítka a hypertextové odkazy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Složené vzory
 Existuje několik způsobů, jak mohou uživatelé provádět úkoly. Ať už je to možné, funkce by měly být navržené tak, aby byly použity jak pro interakce, tak pro vizuální návrh.

 I když v sadě Visual Studio existuje mnoho složených vzorů, některé z nejdůležitějších z hlediska konzistence jsou:

- [Složené vzory pro Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Uživatelské rozhraní pro objekty a prohlížení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modely výběru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Nastavení trvalosti a ukládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Dotykové zadání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
