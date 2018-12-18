---
title: Zdroje Essentials integrace ovládacího prvku | Dokumentace Microsoftu
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
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9893d5525bf66b167dea170c0c5fae8285aa40af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780968"
---
# <a name="source-control-integration-essentials"></a>Základy integrace správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporuje dva typy integrace správy zdrojového kódu: správy zdrojového kódu modulu plug-in, který poskytuje základní funkce a je vytvořená pomocí rozhraní API modulu Plug-in zdroje ovládacího prvku (dříve označované jako rozhraní API MSSCCI) a řešení pro integraci na základě balíčku VSPackage zdrojového ovládacího prvku, který poskytuje robustnější funkce.  
  
## <a name="source-control-plug-in"></a>Modul Plug-in správy zdrojového kódu  
 Plug-in ovládací prvek zdroje je zapsán jako knihovnu DLL, která implementuje rozhraní API modulu Plug-in zdroje ovládacího prvku. Registrace a zdroj funkce integrace ovládacího prvku je poskytovaná prostřednictvím rozhraní API. Tento přístup je jednodušší než balíčku VSPackage správy zdrojového kódu implementace a používá [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatelského rozhraní (UI) pro většinu operací správy zdrojů.  
  
 K implementaci modulu plug-in pomocí rozhraní API pro zdrojový ovládací prvek modulu Plug-in správy zdrojového kódu, postupujte podle těchto kroků:  
  
1. Vytvořit knihovnu DLL, která implementuje funkcí zadaných v [moduly plug-in správy zdrojových kódů](../../extensibility/source-control-plug-ins.md).  
  
2. Zaregistruje knihovnu DLL tak, že položky registru, jak je popsáno v [postupy: Instalace modulu Plug-in zdrojového ovládacího prvku](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Vytvořit pomocné rutiny uživatelského rozhraní a zobrazit ji po zobrazení výzvy zdrojový balíček adaptér ovládací prvek ( [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komponenta, která zpracovává funkce správy zdrojového kódu pomocí ovládacího prvku moduly plug-in zdrojového kódu).  
  
   Další informace najdete v tématu [vytváření modulu Plug-in zdrojového ovládacího prvku](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Ovládací prvek zdroje balíčku VSPackage  
 Implementace balíčku VSPackage správy zdrojového kódu umožňuje vyvíjet přizpůsobené náhrada za [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zdrojového ovládacího prvku uživatelského rozhraní. Tento přístup poskytuje úplnou kontrolu nad integrace správy zdrojového kódu, ale vyžaduje, aby poskytoval prvky uživatelského rozhraní a implementaci rozhraní pro řízení zdroje, které by jinak poskytované v rámci modulu plug-in přístup.  
  
 Pokud chcete implementovat balíčku VSPackage správy zdrojového kódu, musíte mít:  
  
1. Vytvořte a zaregistrujte vlastní ovládací prvek zdroje balíčku VSPackage, jak je popsáno v [registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Nahraďte výchozí zdrojový ovládací prvek uživatelského rozhraní vlastního uživatelského rozhraní. Zobrazit [vlastní uživatelské rozhraní](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Zadejte symboly, které se dá použít a zpracování **Průzkumníka řešení** piktogram události. Zobrazit [piktogramů](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Zpracování událostí dotazu upravit a uložit dotaz, jak je znázorněno v [dotaz upravit dotaz uložit](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
   Další informace najdete v tématu [vytváření VSPackage ovládací prvek zdroje](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled](../../extensibility/internals/source-control-integration-overview.md)   
 [Vytvoření modulu Plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)

