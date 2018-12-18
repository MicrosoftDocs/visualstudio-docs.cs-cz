---
title: Průvodce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbf2eceeb3ae8a3870954d53f8d85c46f3322d24
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747588"
---
# <a name="wizards"></a>Průvodci
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po vytvoření průvodce obvykle chcete a přidejte ji tak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE) tak, aby ho ostatní mohli používat. Přidání průvodce se pak objeví v **přidat nový projekt** nebo **přidat novou položku** dialogových oknech. Chcete-li zobrazit **přidat nový projekt** nebo **přidat novou položku** dialogové okno polí klikněte pravým tlačítkem na řešení otevřeného v **Průzkumníku řešení**, přejděte na **přidat**, a pak klikněte na tlačítko **nový projekt** nebo **nová položka**.  
  
 Průvodce je možné implementovat v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] umožňuje uživatelům vyberte ze stromu zobrazení dostupných hodnot při otevření **přidat nový projekt** dialogové okno nebo **přidat novou položku** dialogové okno, nebo když, klikněte pravým tlačítkem na položky v **Průzkumníka řešení**.  
  
 V průvodci můžete zadat možnost lokalizace název nového projektu nebo ites a můžete určit ikonu, která uživatelům se zobrazí, když vyberou průvodce. Můžete také řídit pořadí, ve kterém se objeví nové položky vzhledem k další položky k dispozici; položky, nemusí být uspořádány podle abecedy.  
  
 Můžete také zadat průvodce, který spustí odlišně, na základě vlastních parametrů, které se předávají při otevření průvodce.  
  
 Témata v této části popisují soubory, které implementují způsobit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **přidat nový projekt** a **přidat novou položku** dialogová okna seznam průvodce mezi dostupných průvodcích a šablony a požadavky, které průvodce musí splňovat pro správnou funkci v integrovaném vývojovém prostředí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Poskytuje přehled o jaké šablony soubory popisu adresáře a vysvětluje, jak fungují v prostředí IDE pro zobrazení složek, souborů průvodce .vsz a souborů šablon, které jsou spojené s projektem v dialogových oknech.  
  
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Vysvětluje, jak spuštění rozhraní IDE průvodců a obsahuje tři části souboru.  
  
 [Rozhraní průvodce (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Popisuje `IDTWizard` rozhraní, které průvodce musí implementovat pracovat v integrovaném vývojovém prostředí.  
  
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)  
 Vysvětluje, jak se implementují průvodců a co se stane, když je integrované vývojové prostředí úspěšné parametry kontextu pro implementaci.  
  
 [Vlastní parametry](../../extensibility/internals/custom-parameters.md)  
 Vysvětluje, jak použít vlastní parametry pro řízení používání průvodce po spuštění průvodce.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Obsahuje odkazy na další témata, která nabízí informace o navrhování nových typů projektů.  
  
 [Návod: Vytvoření průvodce](http://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Ukazuje, jak vytvořit průvodce.  
  
 [Rozšíření projektů](../../extensibility/extending-projects.md)  
 Popisuje způsob použití [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekty a řešení pro uspořádání souborů s kódem a soubory prostředků a jak implementovat správy zdrojového kódu.

