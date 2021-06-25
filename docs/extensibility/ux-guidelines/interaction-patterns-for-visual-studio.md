---
title: Vzory interakce pro Visual Studio | Microsoft Docs
description: Seznamte se s knihovnou běžných vzorů interakce, které můžete použít při vytváření nových funkcí pro Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a2ec4332cf8010dc5d214dfd61936725ac2063
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900548"
---
# <a name="interaction-patterns-for-visual-studio"></a>Vzory interakcí pro Visual Studio
## <a name="overview"></a>Přehled
 Vzor návrhu je obecně jádrem návrhu, který lze použít v určitých situacích k řešení problémů s podobnými sadami omezení. Návrháři funkcí a systémů používají tyto vzory návrhu jako výchozí body, které je pak možné přizpůsobit jejich konkrétní situaci.

 Visual Studio má knihovnu běžných vzorů interakce, které by se měly zvážit při vytváření nových funkcí. Pro naše vzory návrhu existují dva základní kontexty: Visual Studio Client (devenv) a GitHub Codespaces (dříve Visual Studio Online). U některých problémů s návrhem existuje všudypřítomný vzor, který funguje dobře ve všech situacích. V mnoha případech se ale řešení může lišit pro uživatelské rozhraní, které se prezentuje v prohlížeči a které je hostované v klientské aplikaci.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio typů vzorů klienta

|Typ vzoru|Description|Příklady|
|------------------|-----------------|--------------|
|**Vzory na úrovni aplikace**|Vzory vysoké úrovně společné pro aplikaci, určování nebo zobrazení kontextu aplikace a obsahující složené vzory a řídicí vzory v nich|– Okna nástrojů<br />– Okna dokumentů|
|**Složené vzory**|Běžné vzory, které mohou zahrnovat různé vzory aplikací nebo rozpoznaný vzor tvořený několika ovládacími prvky v odlišné konfiguraci|– Přepínání zobrazení<br />– Tvůrci seznamu<br />– Zobrazení dat<br />– Oznámení<br />– Ověření<br />– Modely výběru|
|**Vzory řízení**|Specifika toho, jak se očekává chování ovládacích prvků nízké úrovně|– Stromová zobrazení<br />– Úpravy v ovládacím prvku mřížky|

## <a name="application-patterns"></a>Vzory aplikací
 Na nejvyšší úrovni se rozhraní Visual Studio více oken, dialogových oken, příkazů a panelů nástrojů v rámci jednoho integrovaného vývojového prostředí (IDE). Hierarchie Visual Studio určuje kontext a řídí nabídky. Klíčovými body integrace v uživatelském rozhraní integrovaného vývojového prostředí jsou okna dokumentů, okna nástrojů, projekty, struktura příkazů, textový editor, panel nástrojů, okno Vlastnosti a Nástroje > Možnosti.

 Pro každý z klíčových bodů integrace v uživatelském rozhraní integrovaného vývojového prostředí existují základní vzory použití:

- [Nabídky a příkazy pro Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Vzory aplikací pro Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interakce oken](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Okna nástrojů](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Konvence editoru dokumentů](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialogy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Běžné vzory ovládacích panelů
 Vzory ovládacích prvků se týkají hlavně toho, jak se jednotlivé ovládací prvky mají chovat. Jedná se o jednu oblast, ve které je konzistence nejdůležitější.

 Nejběžnější ovládací prvky v Visual Studio by se měly řídit pokyny pro Desktop Windows. Naše pokyny zahrnují pouze oblasti, ve kterých potřebujeme rozšířit běžné konvence o interakce specifické pro konkrétní uživatele, Visual Studio místa, ve kterých pokyny zcela nahrazujeme, abychom mohli přizpůsobit Visual Studio tak, aby splňovaly potřeby našich sofistikovaných uživatelů.

- [Vzory běžných ovládacích prvků pro Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Běžné ovládací prvky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Textové ovládací prvky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Tlačítka a hypertextové odkazy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Složené vzory
 Existuje několik způsobů, jak uživatelé očekávají, že budou provádět úkoly. Všude, kde je to možné, by měly být funkce navrženy tak, aby tyto vzory byly navrženy pro interakci i vizuální návrh.

 I když existuje mnoho složených vzorů Visual Studio, některé z nejdůležitějších v souvislosti s konzistencí jsou:

- [Složené vzory pro Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Uživatelské rozhraní pro objekty a prohlížení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modely výběru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Nastavení trvalosti a ukládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Dotykové zadání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
