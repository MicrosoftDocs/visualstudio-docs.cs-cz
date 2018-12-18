---
title: Interakce vzory pro sadu Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142429"
---
# <a name="interaction-patterns-for-visual-studio"></a>Interakce vzory pro sadu Visual Studio
## <a name="overview"></a>Přehled  
 Návrhový vzor, obecně je základní návrh, který lze použít v konkrétních situacích k řešení problémů s podobnou sadu omezení. Funkce a systému návrháři používají tyto vzory návrhu jako výchozí body, které můžou být přizpůsobena jejich konkrétní situaci.  
  
 Visual Studio obsahuje knihovnu běžných vzorů interakce, které je potřeba zvážit při vytváření nové funkce. Existují dva základní kontexty pro naše vzory návrhu: klienta Visual Studia (devenv) a Visual Studio Online. Pro některé problémy návrhu je všudypřítomný vzor, který skvěle funguje ve všech situacích. V mnoha případech ale řešení může být různé pro uživatelské rozhraní, které se zobrazí v prohlížeči a který, který je hostován na klientskou aplikaci.  
  
### <a name="visual-studio-client-pattern-types"></a>Visual Studio klienta vzor typy  
  
|Typ vzor|Popis|Příklady|  
|------------------|-----------------|--------------|  
|**Vzory úrovni aplikace**|Podrobný vzorů, které jsou společné pro aplikace, určení nebo zobrazení kontextu aplikací a obsahující složené a řízení vzory v nich|– Windows nástroje<br />-Document windows|  
|**Složené vzory**|Obecné vzory zahrnující napříč vzory aplikace nebo rozpoznaný vzor skládá z několika ovládacích prvků v odlišné konfigurace|– Přepínání zobrazení<br />-List počítačů<br />-Zobrazení dat<br />– Oznámení<br />– Ověření<br />-Výběr modely|  
|**Vzory ovládacích prvků**|Podrobnosti o tom, jak nízké úrovně ovládací prvky budou chovat|-Stromové zobrazení<br />-Úpravy v rámci ovládacího prvku mřížky|  
  
## <a name="application-patterns"></a>Vzory aplikace  
 Na vysoké úrovni rozhraní sady Visual Studio se skládá z více windows, dialogová okna, příkazy a panelů nástrojů v rámci jedné IDE. V sadě Visual Studio hierarchii určuje kontextu a jednotky nabídky. Klíče integrace body v uživatelském rozhraní IDE jsou okna dokumentu, nástroj windows, projekty, příkazovou strukturu, textový editor, sady nástrojů, vlastnosti – okno a nástroje > Možnosti.  
  
 Existují vzory základní informace o využití pro každou bodů klíče integrace v uživatelském rozhraní IDE:  
  
-   [Nabídek a příkazů pro sadu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Aplikace vzory pro sadu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Okno interakce](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Nástroje systému windows](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Konvence pro dokumenty editoru](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Dialogy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Běžné vzory ovládacích prvků  
 Vzory ovládacích prvků jsou hlavně o tom, jak jednotlivých ovládacích prvcích budou chovat. Toto je jedna oblast, ve kterém je nejdůležitější konzistence.  
  
 Většina běžných ovládacích prvků v sadě Visual Studio by měl postupujte podle pokynů plochy Windows. Naše pokyny zahrnují jenom oblasti, ve kterých je potřeba posílení běžné konvence s Visual Studio specifické interakce nebo místa, ve kterých jsme nahrazují pokynů zcela Chcete-li přizpůsobit Visual Studio, aby vyhovovaly sofistikované uživateli.  
  
-   [Běžné vzory ovládacích prvků pro sadu Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Běžné ovládací prvky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Ovládacích prvků textu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Tlačítka a hypertextové odkazy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Složené vzory  
 Existuje několik způsobů, jak uživatelé očekávají, že k provádění úloh. Pokud je to možné, funkce by měl být pro použijte tyto vzorce pro interakci i visual návrhu.  
  
 Když dochází k mnoha složené schémat v sadě Visual Studio, některé z vašich nejdůležitějších s ohledem na konzistence jsou:  
  
-   [Složené vzory pro sadu Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Na objekt uživatelského rozhraní a prohlížení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Výběr modely](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Trvalosti a ukládá se nastavení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Dotykové ovládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)