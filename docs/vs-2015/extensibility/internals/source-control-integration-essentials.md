---
title: Základy integrace správy zdrojového kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b9189b647baa29d72975f84172696ecb54cd7f87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183436"
---
# <a name="source-control-integration-essentials"></a>Základy integrace správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporuje dva typy integrace správy zdrojového kódu: modul plug-in správy zdrojového kódu, který poskytuje základní funkce a je sestaven pomocí rozhraní API modulu plug-in správy zdrojových kódů (dříve označovaného jako rozhraní MSSCCI API) a řešení integrace správy zdrojového kódu založeného na VSPackage, které poskytuje robustnější funkce.  
  
## <a name="source-control-plug-in"></a>Modul plug-in správy zdrojového kódu  
 Modul plug-in správy zdrojových kódů je napsán jako knihovna DLL, která implementuje rozhraní API modulu plug-in správy zdrojového kódu. Funkce registrace a integrace správy zdrojového kódu se poskytuje prostřednictvím rozhraní API. Tento přístup je snazší implementovat než balíček VSPackage správy zdrojového kódu a používá [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatelské rozhraní (UI) pro většinu operací správy zdrojového kódu.  
  
 Chcete-li implementovat modul plug-in správy zdrojových kódů pomocí rozhraní API modulu plug-in správy zdrojového kódu, postupujte následovně:  
  
1. Vytvořte knihovnu DLL, která implementuje funkce určené v [modulu plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md).  
  
2. Zaregistrujte knihovnu DLL tak, že provedete příslušné položky registru, jak je popsáno v tématu [Postupy: Instalace modulu plug-in správy zdrojových kódů](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Vytvořte pomocné uživatelské rozhraní a zobrazte ho po zobrazení výzvy balíčkem adaptéru správy zdrojového kódu ( [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] součást, která zpracovává funkce správy zdrojového kódu prostřednictvím modulů plug-in správy zdrojových kódů).  
  
   Další informace naleznete v tématu [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>VSPackage správy zdrojového kódu  
 Implementace balíčku VSPackage správy zdrojového kódu umožňuje vývoj vlastního nahrazení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatelského rozhraní správy zdrojového kódu. Tento přístup poskytuje úplnou kontrolu nad integrací správy zdrojového kódu, ale vyžaduje, abyste zadali prvky uživatelského rozhraní a implementovali rozhraní správy zdrojového kódu, která by jinak byla poskytnuta v rámci přístupu modulu plug-in.  
  
 K implementaci balíčku VSPackage správy zdrojového kódu musíte:  
  
1. Vytvořte a zaregistrujte si vlastní VSPackage správy zdrojového kódu, jak je popsáno v tématu [registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Nahraďte výchozí uživatelské rozhraní správy zdrojového kódu vlastním uživatelským ROZHRANÍm. Viz [vlastní uživatelské rozhraní](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Určete glyfy, které se mají použít, a zpracujte **Průzkumník řešení** události glyfů. Viz [ovládací prvek glyf](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Zpracování událostí úprav dotazů a dotazech na uložení, jak je znázorněno v dotazech pro [úpravu](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)dotazu.  
  
   Další informace najdete v tématu [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled](../../extensibility/internals/source-control-integration-overview.md)   
 [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)
