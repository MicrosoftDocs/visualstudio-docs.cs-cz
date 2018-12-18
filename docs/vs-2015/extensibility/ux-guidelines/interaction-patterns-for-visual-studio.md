---
title: Vzory interakcí
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f77848babfbddc4d12ac6d599c8e77d2b598534
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053309"
---
# <a name="interaction-patterns-for-visual-studio"></a>Vzory interakcí pro sadu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="overview"></a>Přehled
 Návrhový vzor, obecně je základní návrh, který lze použít v určitých situacích k řešení problémů s podobnými sadami omezení. Funkce a systémové návrháři používají tyto způsoby návrhu jako výchozí body, které mohou být upraveny tak, aby jejich konkrétní situaci.

 Visual Studio obsahuje knihovnu běžných vzorů interakce, měli byste zvážit při vytváření nových funkcí. Existují dva základní kontexty pro naše vzory návrhu: Visual Studio klienta (devenv) a Visual Studio Online. Některé potíže s návrhem je všudypřítomná vzor, který funguje dobře ve všech situacích. V mnoha případech ale řešení může být různé pro uživatelské rozhraní zobrazené v prohlížeči a které je hostované v klientské aplikaci.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio klienta vzor typy

|Typ vzorku|Popis|Příklady|
|------------------|-----------------|--------------|
|**Modely na úrovni aplikace**|Základní vzorce, které jsou společné pro aplikace, určení nebo zobrazení kontext aplikace a obsahující složeného a ovládací prvek vzorů v rámci jejich|– Windows nástroje<br />– Dokument windows|
|**Složené vzory**|Běžné vzory, které můžou pokrývat vzory aplikací nebo vzor rozpoznaný skládá z několika ovládacích prvků v odlišné konfigurace|– Přepínání zobrazení<br />-Tvůrci list<br />– Zobrazení dat<br />– Oznámení<br />– Ověření<br />-Výběr modely|
|**Vzory ovládacích prvků**|Podrobnosti o tom, jak nízké úrovně ovládacích prvcích očekává se chovají|-Stromová zobrazení<br />-Úpravy v rámci ovládací prvek mřížky|

## <a name="application-patterns"></a>Vzory aplikací
 Na vysoké úrovni rozhraní sady Visual Studio se skládá z několika windows, dialogová okna, příkazy a panelů nástrojů v jediném integrovaném vývojovém prostředí. Hierarchie sady Visual Studio určuje kontext a jednotky nabídky. Klíče integrační body v uživatelském rozhraní IDE se oken dokumentů, oken nástrojů, projektů, příkazovou strukturu, textový editor, sady nástrojů, okno Vlastnosti a nástroje > Možnosti.

 Existují vzory základní informace o využití pro jednotlivé body klíčové integrace v uživatelském rozhraní IDE:

-   [Nabídky a příkazy pro Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

-   [Vzory aplikací pro Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

    -   [Okno interakce](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

    -   [Nástroje systému windows](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

    -   [Konvence pro dokumenty editoru](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

    -   [Dialogy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

    -   [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Vzory běžných ovládacích prvků
 Vzory ovládacích prvků se hlavně o využití jednotlivých ovládacích prvcích očekává se chovají. Toto je jednu oblast, ve kterém je nejdůležitější konzistence.

 Většina běžných ovládacích prvků v sadě Visual Studio by měl postupovat podle pokynů Windows Desktop. Naše pokyny zahrnují jenom oblasti, ve kterých potřebujeme k posílení běžné konvence s Visual Studio konkrétní interakce nebo místa, ve kterých jsme mají přednost před pokyny zcela k přizpůsobení sady Visual Studio pro potřeby naše zkušené uživatele.

-   [Vzory běžných ovládacích prvků pro Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

    -   [Běžné ovládací prvky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

    -   [Textových ovládacích prvků](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

    -   [Tlačítka a hypertextových odkazů](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Složené vzory
 Existuje mnoho způsobů, jak uživatelé očekávají, že k provádění úloh. Kdykoli je to možné, měly být navrhované funkce s využitím těchto vzorů pro interakce i vizuálním návrhem.

 I když existují mnoho složené vzory v sadě Visual Studio, některé z vašich nejdůležitějších s ohledem na konzistenci jsou:

-   [Složené vzory pro Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

    -   [Na objekt uživatelského rozhraní a prohlížení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

    -   [Výběr modely](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

    -   [Trvalost a ukládají se nastavení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

    -   [Dotykové ovládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
