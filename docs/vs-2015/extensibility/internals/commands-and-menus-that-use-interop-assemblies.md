---
title: Příkazy a nabídky používající definiční sestavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195047"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Příkazy a nabídky, které používají definiční sestavení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage, který implementuje příkazy nabídky a panelu nástrojů pomocí sestavení interop, musí:  
  
- Informujte [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) o podporovaných příkazech a o tom, jestli jsou momentálně povolené.  
  
- Dodržovat pravidla (kontrakt) pro zpracování příkazů.  
  
- Explicitně implementujte zpracování příkazů pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> rozhraní nebo.  
  
  Následující článek popisuje, jak provádět tyto úlohy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Určení stavu příkazu pomocí definičních sestavení](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Popisuje, jakým způsobem VSPackage oznamuje rozhraní IDE, které příkazy podporuje a zda jsou aktuálně povoleny.  
  
 [Kontrakty příkazů v definičních sestaveních](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Poskytuje definici základní kontraktu příkazu, který používají všechny sady VSPackage implementující příkazy pomocí sestavení Interop.  
  
 [Implementace](../../extensibility/internals/command-implementation.md)  
 Poskytuje přehled o tom, jak VSPackage implementuje příkaz.  
  
 [Registrace obslužných rutin příkazů definičních sestavení](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Popisuje položky registru potřebné pro oznamování integrovanému vývojovému prostředí (IDE), které rozhraní VSPackage poskytuje obslužnou rutinu příkazu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Dostupnost](../../extensibility/internals/command-availability.md)  
 Popisuje kritéria, která jsou používána rozhraním IDE k určení, které příkazy VSPackage jsou k dispozici a které objekt je zpracovává.  
  
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Obsahuje podrobné informace o tom, jak vytvořit uživatelské rozhraní, které používá [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporu příkazů.  
  
 [Směrování příkazů v balíčcích VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Přehled procesu sloužícího k přidružení objektu ke správné žádosti o příkaz.
