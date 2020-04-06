---
title: Vzory interakce pro visual studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698379"
---
# <a name="interaction-patterns-for-visual-studio"></a>Vzory interakcí pro Visual Studio
## <a name="overview"></a>Přehled
 Návrhový vzor je obecně jádrem návrhu, který lze použít v konkrétních situacích k řešení problémů s podobnými sadami omezení. Návrháři funkcí a systémů používají tyto návrhové vzory jako výchozí body, které pak mohou být přizpůsobeny jejich konkrétní situaci.

 Visual Studio má knihovnu společné interakce vzory, které by měly být považovány při vytváření nových funkcí. Existují dva základní kontexty pro naše návrhové vzory: Visual Studio Client (devenv) a Visual Studio Online. Pro některé problémy s návrhem existuje všudypřítomný vzor, který funguje dobře ve všech situacích. V mnoha případech se však řešení může lišit pro uhlavního použití, které je prezentováno v prohlížeči a které je hostováno v klientské aplikaci.

### <a name="visual-studio-client-pattern-types"></a>Typy vzorů klienta Visual Studio

|Typ vzorku|Popis|Příklady|
|------------------|-----------------|--------------|
|**Vzory na úrovni aplikace**|Vzory na vysoké úrovni společné pro aplikaci, určení nebo zobrazení kontextu aplikace a obsahující složené a řídicí vzory v nich|- Okna nástrojů<br />- Okna dokumentů|
|**Složené vzorky**|Běžné vzory, které se mohou rozprostírat napříč vzory aplikací nebo rozpoznaný vzor tvořený několika ovládacími prvky v odlišné konfiguraci|- Přepínání zobrazení<br />- Seznam stavitelé<br />- Zobrazení dat<br />- Oznámení<br />- Validace<br />- Výběrové modely|
|**Vzory ovládacího prvku**|Podrobnosti o tom, jak se mají nízkoúrovňové kontroly chovat|- Pohledy na stromy<br />- Editace v rámci ovládacího prvku mřížky|

## <a name="application-patterns"></a>Vzory aplikací
 Na vysoké úrovni rozhraní sady Visual Studio obsahuje více oken, dialogových oken, příkazů a panelů nástrojů v rámci jednoho rozhraní IDE. Hierarchie sady Visual Studio určuje kontext a řídí nabídky. Klíčovými integračními body v uživatelském rozhraní rozhraní IDE jsou okna dokumentů, okna nástrojů, projekty, struktura příkazů, textový editor, panel nástrojů, okno Vlastnosti a možnosti > nástroje.

 Existují základní vzorce použití pro každý z klíčových integračních bodů v uživatelském rozhraní rozhraní IDE:

- [Nabídky a příkazy pro Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Vzory aplikací pro Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interakce s okny](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Okna nástrojů](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Konvence editoru dokumentů](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialogy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Běžné vzory ovládacích prvku
 Vzory ovládacích prvků jsou hlavně o tom, jak se očekává, že se jednotlivé ovládací prvky budou chovat. To je jedna z oblastí, ve kterých konzistence je nejdůležitější.

 Nejběžnější ovládací prvky v sadě Visual Studio by měly dodržovat pokyny pro systém Windows pro stolní počítače. Naše pokyny zahrnují pouze oblasti, ve kterých potřebujeme rozšířit společné konvence s interakcí specifické pro Visual Studio nebo místa, ve kterých nahrazujeme pokyny zcela s cílem přizpůsobit Visual Studio tak, aby vyhovovaly potřebám našich sofistikovaných uživatelů.

- [Vzory běžných ovládacích prvků pro Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Běžné ovládací prvky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Ovládací prvky textu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Tlačítka a hypertextové odkazy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Složené vzorky
 Existuje několik způsobů, které uživatelé očekávají k provedení úkolů. Kdykoli je to možné, měly by být prvky navrženy tak, aby tyto vzory používaly jak pro interakci, tak pro vizuální návrh.

 Zatímco existuje mnoho složené vzory v rámci sady Visual Studio, některé z nejdůležitějších s ohledem na konzistenci jsou:

- [Složené vzory pro Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [UI na objektu a prohlížení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Výběrové modely](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Nastavení trvalosti a ukládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Dotykové ovládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
