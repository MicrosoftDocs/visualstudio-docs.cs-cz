---
title: Určení, jestli se má implementovat VSPackage správy zdrojového kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cff53700dcd6a80f841108d5a2b486dcb0ba7a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196800"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Určení toho, jestli se má implementovat balíček VSPackage správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V této části se dozvíte, jak moduly plug-in správy zdrojových kódů a sady VSPackage správy zdrojového kódu rozšiřují řešení správy zdrojového kódu, a poskytuje obecné pokyny k výběru vhodné cesty pro integraci.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Řešení malého zdrojového řízení s omezenými prostředky  
 Máte-li omezené prostředky a nelze je zatěžovat s režií psaní balíčku zdrojového kódu, můžete vytvořit moduly plug-in založené na rozhraní API pro správu zdrojového kódu. To vám umožní pracovat souběžně s balíčky správy zdrojového kódu a můžete přepínat mezi moduly plug-in správy zdrojového kódu a balíčky na vyžádání. Další informace najdete v tématu [registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Rozsáhlé řešení správy zdrojového kódu s bohatou sadou funkcí  
 Pokud chcete implementovat řešení správy zdrojového kódu, které poskytuje bohatou správu zdrojového kódu, která není vhodně zachycena pomocí rozhraní API modulu plug-in správy zdrojového kódu, můžete zvážit balíček správy zdrojového kódu jako cestu pro integraci. To platí hlavně v případě, že byste nahradili balíček adaptéru správy zdrojového kódu (který komunikuje s moduly plug-in správy zdrojových kódů a poskytuje základní uživatelské rozhraní pro správu zdrojového kódu) vlastními možnostmi, abyste mohli zpracovávat události správy zdrojového kódu vlastním způsobem. Pokud již máte dostatečné uživatelské rozhraní správy zdrojových kódů a chcete zachovat toto prostředí v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , možnost balíčku správy zdrojového kódu vám umožní pouze to. Balíček správy zdrojového kódu není obecný a je určený výhradně pro použití s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředím IDE.  
  
 Pokud chcete implementovat řešení správy zdrojového kódu, které poskytuje flexibilitu a lepší kontrolu nad logikou a uživatelským rozhraním správy zdrojového kódu, můžete upřednostnit postup integrace balíčku správy zdrojového kódu. Další možnosti:  
  
1. Zaregistrujte si vlastní VSPackage správy zdrojového kódu (viz [registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2. Nahraďte výchozí uživatelské rozhraní správy zdrojového kódu vlastním uživatelským ROZHRANÍm (viz [vlastní uživatelské rozhraní](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3. Zadejte glyfy, které se mají použít, a zpracujte Průzkumník řešení události glyfů (viz [ovládací prvek glyf](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4. Zpracování událostí úprav dotazů a dotazů na uložení dotazu (viz [dotaz pro úpravu](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)dotazu pro úpravy)  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
