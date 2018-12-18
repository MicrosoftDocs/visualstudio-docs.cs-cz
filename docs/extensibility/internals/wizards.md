---
title: Průvodci | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03cee9de14da76ea65882d906acb3af88e72e999
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138711"
---
# <a name="wizards"></a>Průvodci
Po vytvoření průvodce, obvykle je vhodné ho přidat do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE), aby ostatní ho používat. Přidání průvodce se potom zobrazí v **přidat nový projekt** nebo **přidat novou položku** dialogová okna. Chcete-li zobrazit **přidat nový projekt** nebo **přidat novou položku** dialogové okno polí, klikněte pravým tlačítkem na otevřete řešení v **Průzkumníku řešení**, přejděte na **přidat**, a pak klikněte na tlačítko **nový projekt** nebo **novou položku**.  
  
 Průvodci, můžou se implementovat v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, aby uživatelé vyberte z strom dostupné hodnoty při otevření **přidat nový projekt** dialogové okno nebo **přidat novou položku** dialogové okno, nebo když se klikněte pravým tlačítkem na položky v **Průzkumníku řešení**.  
  
 V průvodci můžete zadat možnost lokalizace název nového projektu nebo ites a můžete určit ikonu, která se zobrazí uživatelům, když vyberou průvodce. Můžete také ovládat pořadí, ve kterém nové položky zobrazí relativně k jiné dostupné položky; položky nemusí být uspořádány podle abecedy.  
  
 Můžete také zadat průvodce, který spustí odlišně, na základě vlastních parametrů, které se předávají při otevření průvodce.  
  
 Témata v této části popisují soubory, které implementují způsobí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **přidat nový projekt** a **přidat novou položku** dialogových oken k zobrazení seznamu průvodce mezi dostupných průvodcích a šablon a požadavky, které průvodce musí splnit, aby správně fungovaly v prostředí IDE.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Poskytuje přehled jakou šablonu soubory popis adresáře a vysvětluje, jak fungují v prostředí IDE pro zobrazení složky, průvodce .vsz soubory a soubory šablony, které jsou spojeny s projektem v dialogových oknech.  
  
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Vysvětluje, jak rozhraní IDE spuštění průvodců a uvádí tyto tři části souboru.  
  
 [Rozhraní průvodce (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Popisuje `IDTWizard` rozhraní, které průvodců musí implementovat, aby fungovaly v prostředí IDE.  
  
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)  
 Vysvětluje, jak jsou implementované průvodců a co se stane, když prostředí IDE předá parametr kontextu pro implementaci.  
  
 [Vlastní parametry](../../extensibility/internals/custom-parameters.md)  
 Vysvětluje, jak chcete používat vlastní parametry řízení činnosti průvodce po spuštění průvodce.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Obsahuje odkazy na další témata, které nabízí informace o tom, jak navrhnout nové typy projektů.  
  
 [Rozšíření projektů](../../extensibility/extending-projects.md)  
 Popisuje způsob použití [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty a řešení pro uspořádání soubory kódu a soubory prostředků a implementaci řízení zdrojů.