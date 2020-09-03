---
title: Rozšiřitelnost služby starší verze jazyka | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9346311aac4bc5833005423e90c2eb92faddcb84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194981"
---
# <a name="legacy-language-service-extensibility"></a>Rozšíření služeb starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jazyková služba poskytuje podporu pro konkrétní jazyk pro úpravu zdrojového kódu v integrovaném vývojovém prostředí.  
  
 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).  
  
 Tato část popisuje strukturu a implementaci služby starší verze jazyka.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Migrace služby starší verze jazyka](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Vysvětluje, jak aktualizovat službu jazyka ze sady Visual Studio 2008 na nejnovější verzi.  
  
 [Základy služby starší verze jazyka](../../extensibility/internals/legacy-language-service-essentials.md)  
 Poskytuje důležité informace o tom, jak vyvíjet jazykové služby pro integraci programovacího jazyka do sady Visual Studio.  
  
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Obsahuje odkazy na témata, která vám pomůžou vytvořit službu jazyka.  
  
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Poskytuje informace o podpoře zvýrazňování syntaxe ve službě jazyka.  
  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Poskytuje informace o tom, jak použít sadu Managed Package Framework (MPF) k implementaci plně funkční jazykové služby ve spravovaném kódu.  
  
 [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Popisuje knihovny a nástroje, které umožňují procházet stromová zobrazení symbolů v integrovaném vývojovém prostředí (IDE).  
  
## <a name="related-sections"></a>Související oddíly  
 [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)  
 Poskytuje přehled editorů sady Visual Studio.  
  
 [Podpora služby jazyka pro ladění](../../extensibility/internals/language-service-support-for-debugging.md)  
 Obsahuje informace o a odkaz na sadu SDK pro ladění sady Visual Studio, která obsahuje informace potřebné k vytvoření a přizpůsobení komponent ladicího programu používaných pro ladění programů.
