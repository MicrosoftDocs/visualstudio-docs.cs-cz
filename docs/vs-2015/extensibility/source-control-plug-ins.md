---
title: Moduly plug-in správy zdrojového | Dokumentace Microsoftu
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
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7c51efc30251a177e07b7acf3e4c62821cb9488
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745458"
---
# <a name="source-control-plug-ins"></a>Moduly plug-in správy zdrojového kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zdrojový ovládací prvek modulu Plug-in SDK odkaz na oddíl obsahuje kompletní rozhraní specifikace, která umožňuje systémy správy zdrojového kódu pro integraci s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Určuje syntaxi a sémantiku různé funkce a datové typy, které modul plug-in správy zdrojového kódu musí implementovat rozhraní s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)  
 Seznam funkcí, které je třeba implementovat modul plug-in správy zdrojového kódu, aby bylo možné v souladu s rozhraním API modulů Plug-in zdroje ovládacího prvku.  
  
 [Funkce zpětného volání implementované integrovaným vývojovým prostředím](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Popisuje funkce, které modul plug-in správy zdrojového kódu se používá k předání informací zpět do integrovaného vývojového prostředí, zatímco některé příkazy provádějí.  
  
 [Enumerátory](../extensibility/enumerators.md)  
 Uvádí výčet datových typů v rozhraní API modulu Plug-in zdroje ovládacího prvku, které musíte znát plug-in správy zdrojových kódů.  
  
 [Příznaky funkcí](../extensibility/capability-flags.md)  
 Popisuje `SCC_CAP_xxx` příznaky, které se označují schopnosti poskytovatele.  
  
 [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)  
 Seznam příznaků, které jsou užitečné v kontextu konkrétní příkazy.  
  
 [Chybové kódy](../extensibility/error-codes.md)  
 Uvádí běžné chybové hodnoty vrácené funkcí jako `SCCTRN`.  
  
 [Řetězce, které slouží jako klíče pro vyhledání modulu plug-in pro správu zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Popisuje klíče pro přístup k registru k vyhledání modulu plug-in správy zdrojového kódu.  
  
 [Soubor MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Popisuje soubor na straně klienta, který obsahuje informace neprůhledné rozhraní IDE, ale modul plug-in správy zdrojového kódu, která je používaná k nalezení řešení nebo projektu ve správě verzí.  
  
 [Osvědčené postupy pro implementaci modulu plug-in zdrojového kódu](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Poskytuje kolekci důležité technické připomenutí pamatovat, když implementujete rozhraní API modulu Plug-in zdroje ovládacího prvku.  
  
 [Omezení délky řetězců](../extensibility/restrictions-on-string-lengths.md)  
 Popisuje omezení v rozhraní API modulu Plug-in zdroje ovládacího prvku na délky řetězce použité v různých funkcí.  
  
 [Glosář](../extensibility/source-control-plug-in-glossary.md)  
 Poskytuje užitečné termíny a jejich definice pro čtení v dokumentaci sady SDK modulu Plug-in zdroje ovládacího prvku.  
  
 [Postupy: Vypnutí upozornění kompatibility pro moduly plug-in zdroje ovládacího prvku](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Popisuje, jak zakázat upozornění.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ukázka modulu Plug-in zdroje ovládacího prvku](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Obsahuje ukázku funkce modulu plug-in správy zdrojového kódu.  
  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Popisuje testovací postupy související s plug-in správy zdrojových kódů.  
  
 [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Tento článek popisuje postup vytvoření správy zdrojového kódu modulu plug-in, který poskytuje funkce správy zdrojového kódu, zatímco používáte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zdrojového ovládacího prvku uživatelského rozhraní (UI).  
  
 [Referenční dokumentace sady Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Zobrazí seznam referenčních témat.

