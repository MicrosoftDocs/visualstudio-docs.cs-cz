---
title: Rozšíření služeb starší verze jazyka | Dokumentace Microsoftu
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
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6481dfd425f549742ad208df0d2cd04dd182c82f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758277"
---
# <a name="legacy-language-service-extensibility"></a>Rozšíření služeb starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Služba jazyka poskytuje podporu konkrétní jazyk pro úpravy zdrojového kódu v rozhraní IDE.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace o nový způsob implementace služby jazyka najdete v tématu [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md).  
  
 Tato část popisuje strukturu a implementace služby starší verze jazyka.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Migrace služby starší verze jazyka](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Vysvětluje, jak aktualizovat službu jazyka ze sady Visual Studio 2008 na nejnovější verzi.  
  
 [Základy služby starší verze jazyka](../../extensibility/internals/legacy-language-service-essentials.md)  
 Poskytuje důležité informace o tom, jak vyvíjet jazykové služby pro integraci programovací jazyk do sady Visual Studio.  
  
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Obsahuje odkazy na témata, které vám pomůžou vytvářet služba jazyka.  
  
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Poskytuje informace o podpoře, zvýrazňování syntaxe ve službě jazyka.  
  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Poskytuje informace o tom, jak používat rozhraní spravovaného balíčku (MPF) k implementaci jazyka plně funkční služba ve spravovaném kódu.  
  
 [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Popisuje knihovny a nástroje, které vám umožní procházet stromu zobrazení symbolů v integrovaném vývojovém prostředí.  
  
## <a name="related-sections"></a>Související oddíly  
 [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)  
 Poskytuje přehled o editory sady Visual Studio.  
  
 [Podpora služby jazyka pro ladění](../../extensibility/internals/language-service-support-for-debugging.md)  
 Poskytuje informace a odkaz na Visual Studio ladění sadu SDK, který obsahuje informace, které je potřeba vytvořit a přizpůsobit komponenty ladicího programu pro ladění programů.

