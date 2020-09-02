---
title: Implementace starší verze jazyka Service1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20493991d8e0740ca045f041e2ba94cf3735ad1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816390"
---
# <a name="implementing-a-legacy-language-service"></a>Implementace služby starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Můžete použít třídy v rozhraní Managed Package Framework (MPF) k implementaci služby starší verze jazyka, která podporuje širokou škálu funkcí, jako je například zvýrazňování syntaxe, shoda se závorkami a dokončování IntelliSense.  
  
 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)  
 Přehled funkcí jazykové služby, které jsou podporovány ve formátu MPF.  
  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Popisuje, co je potřeba k implementaci jazykové služby pomocí možnosti MPF.  
  
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Popisuje kroky, které jsou požadovány k registraci služby jazyka založeného na formátu MPF pomocí nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Popisuje dva analyzátory, které jsou požadovány k implementaci všech funkcí jazykové služby pomocí vlastnosti MPF.  
  
 [Návod: Vytvoření služby starší verze jazyka](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Poskytuje základní kroky, které jsou nutné k implementaci služby MPF jazyka ve VSPackage.  
  
 [Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Ukazuje techniky získání seznamu nainstalovaných fragmentů kódu.  
  
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)  
 Obsahuje odkazy na témata, která podrobně popisují, co je třeba provést k implementaci všech funkcí jazykové služby pomocí funkce MPF.
