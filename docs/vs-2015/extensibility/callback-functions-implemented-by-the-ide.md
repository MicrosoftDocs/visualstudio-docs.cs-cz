---
title: Funkce zpětného volání implementované integrovaným vývojovým prostředím | Dokumentace Microsoftu
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
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d2bf114a22419e5ed4621db52a68d266e2e7d0e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807519"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkce zpětného volání implementované integrovaným vývojovým prostředím
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby integrace s integrované vývojové prostředí (IDE) jako bezproblémové nejrychleji a poskytovat jednotné koncových uživatelů, modul plug-in správy zdrojového kódu můžete použít funkce zpětného volání implementované integrovaným vývojovým prostředím. Modul plug-in může volat tyto funkce ve vhodných chvílích při operaci správy zdrojových kódů k předávání informací do integrovaného vývojového prostředí; integrované vývojové prostředí můžete tyto informace zobrazit jako vložené prvky v jeho nativním uživatelským rozhraním. Uživatel má méně fragmentované prostředí v tomto scénáři než hodnotě modulu plug-in použijí své vlastní uživatelské rozhraní.  
  
 Požadovaný hlavičkový soubor je scc.h. Výchozí umístění je \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Je také v programu VSIP složku, která má ukázka modulu plug-in zdroje ovládacího prvku na \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Popisuje funkce zpětného volání, který používá [sccopenproject –](../extensibility/sccopenproject-function.md) pro zobrazení zpráv ze správy zdrojového kódu modulu plug-in pomocí integrovaného vývojového prostředí.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Popisuje funkce zpětného volání, který používá [sccpopulatelist –](../extensibility/sccpopulatelist-function.md) Při integrovaném vývojovém prostředí nemá úplný přístup k informacím, které je k dispozici pouze plug-in správy zdrojových kódů, jako je například kompletní seznam souborů v systému správy verzí.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Popisuje funkce zpětného volání používané [sccquerychanges –](../extensibility/sccquerychanges-function.md) operace.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Popisuje funkce zpětného volání používané [sccpopulatedirlist –](../extensibility/sccpopulatedirlist-function.md) operace.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Popisuje nastavení voláním funkce zpětného volání [sccsetoption –](../extensibility/sccsetoption-function.md) , která umožňuje komunikovat, název změny zpět do integrovaného vývojového prostředí modulu plug-in správy zdrojového kódu.  
  
## <a name="related-sections"></a>Související oddíly  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Otevře se projekt.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Zkontroluje seznam souborů pro jejich aktuální stav. Kromě toho používá `pfnPopulate` funkce oznámit volajícímu, soubor neodpovídá kritériím pro `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Zkontroluje seznam adresářů a souborů v projektu nebo v projektech, které jsou pod správou zdrojových kódů. Každý název adresáře a souboru nalezena je předán funkci zpětného volání.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Prozkoumá změn názvů, které byly provedeny seznam souborů. Každý název souboru je předán funkci zpětného volání společně s jeho změna stavu.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Nastaví širokou škálu možností. Jednotlivé možnosti začíná `SCC_OPT_xxx` a má vlastní definované sady hodnot.  
  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)  
 Popisuje obsah části reference sady SDK modulu Plug-in zdroje ovládacího prvku.

