---
title: Vytvoření balíčku VSPackage správy zdrojového kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196952"
---
# <a name="creating-a-source-control-vspackage"></a>Vytvoření balíčku VSPackage správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato dokumentace obsahuje odkazy na přehled architektury balíčku pro správu zdrojového kódu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , který je integrovaný s, rozhraní API definované rozhraními, která se mají implementovat, a služby, které se mají využít, a ukázku, která ilustruje jednoduchou implementaci balíčku správy zdrojového kódu.  
  
 Pomocí balíčku VSPackage správy zdrojového kódu můžete vytvořit hloubkovou integrační cestu pro správu zdrojového kódu, se kterou chcete integrovat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Umožňuje balíčku obejít výchozí uživatelské rozhraní správy zdrojového kódu hostované nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , reagovat na požadavky na správu zdrojového kódu v systému projektu a interagovat s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komponentami, jako je **Průzkumník řešení**. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umožňuje partnerům pomocí mechanismu vytvořit VSPackage, který se dá integrovat s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] použitím modelu služby.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Popisuje balíček správy zdrojového kódu, což je pokročilejší alternativa k modulu plug-in správy zdrojových kódů pro implementaci funkcí správy zdrojového kódu v nástroji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Architektura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Prezentuje diagram a vysvětluje komponenty balíčku správy zdrojového kódu.  
  
 [Funkce](../../extensibility/internals/source-control-vspackage-features.md)  
 Popisuje různé funkce balíčku správy zdrojového kódu.  
  
 [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Popisuje strukturu VSPackage, kterou musí balíček správy zdrojového kódu implementovat pro rozsáhlou integraci.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Popisuje, jak vytvořit modul plug-in správy zdrojového kódu, který poskytuje funkce správy zdrojového kódu v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatelském rozhraní správy zdrojového kódu (UI).  
  
 [Správa zdrojového kódu](../../extensibility/internals/source-control.md)  
 Popisuje možnosti pro implementaci správy zdrojového kódu jako integrované funkce nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
