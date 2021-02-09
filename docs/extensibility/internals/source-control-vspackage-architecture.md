---
title: Architektura balíčku VSPackage správy zdrojového kódu | Microsoft Docs
description: Seznamte se s architekturou balíčku pro správu zdrojového kódu, což je VSPackage, který poskytuje funkce pro sadu Visual Studio jako službu správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e4de5f46746f79e1c7598e1c2a2a6af6ae1d92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912685"
---
# <a name="source-control-vspackage-architecture"></a>Architektura balíčku VSPackage správy zdrojového kódu
Balíček správy zdrojového kódu je VSPackage, který používá služby, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje rozhraní IDE. V případě, že balíček správy zdrojového kódu poskytuje své funkce jako službu správy zdrojového kódu. Balíček pro správu zdrojového kódu je navíc všestrannější alternativou než modul plug-in správy zdrojového kódu pro integraci správy zdrojového kódu do nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Modul plug-in správy zdrojových kódů, který implementuje rozhraní API modulu plug-in správy zdrojového kódu společnost striktní smlouvou. Například modul plug-in nemůže nahradit výchozí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelské rozhraní (UI). Kromě toho rozhraní API modulu plug-in správy zdrojového kódu nepovoluje modul plug-in pro implementaci vlastního modelu správy zdrojového kódu. Balíček pro správu zdrojového kódu ale přesměruje obě tato omezení. Balíček správy zdrojového kódu má úplnou kontrolu nad prostředím pro správu zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatele. Kromě toho balíček správy zdrojového kódu může použít svůj vlastní model a logiku správy zdrojového kódu a může definovat všechna uživatelská rozhraní související se správou zdrojových kódů.

## <a name="source-control-package-components"></a>Součásti balíčku Source-Control
 Jak je znázorněno v diagramu architektury, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenta s názvem zástupná procedura správy zdrojového kódu je VSPackage, který integruje balíček zdrojového kódu s nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Zástupný kód správy zdrojového kódu zpracovává následující úkoly.

- Poskytuje společné uživatelské rozhraní, které je vyžadováno pro registraci balíčku správy zdrojového kódu.

- Načte balíček správy zdrojového kódu.

- Nastaví balíček správy zdrojového kódu jako aktivní nebo neaktivní.

  Zástupný kód správy zdrojového kódu hledá aktivní službu pro balíček zdrojového kódu a směruje všechna volání příchozích služeb z integrovaného vývojového prostředí do daného balíčku.

  Balíček adaptéru správy zdrojového kódu je speciální balíček pro správu zdrojového kódu, který [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje. Tento balíček je centrální součástí pro podporu modulů plug-in pro správu zdrojového kódu na základě rozhraní API modulu plug-in správy zdrojového kódu. Když je modul plug-in správy zdrojového kódu aktivní modulem plug-in, odešle zástupný kód správy zdrojového kódu své události do balíčku adaptéru správy zdrojového kódu. Balíček adaptéru správy zdrojového kódu pak komunikuje s modulem plug-in správy zdrojových kódů pomocí rozhraní API modulu plug-in správy zdrojového kódu a také poskytuje výchozí uživatelské rozhraní, které je běžné pro všechny moduly plug-in správy zdrojového kódu.

  Když je balíček správy zdrojového kódu aktivním balíčkem, je na druhé straně zástupný kód správy zdrojového kódu přímo komunikuje s balíčkem pomocí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] rozhraní Source-Control balíčku. Balíček Source-Control zodpovídá za hostování vlastního uživatelského rozhraní správy zdrojového kódu.

  ![Grafika architektury správy zdrojového kódu](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Pro balíček správy zdrojového [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kódu neposkytuje integraci kód správy zdrojového kódu ani rozhraní API. Na rozdíl od toho s přístupem popsaným v části [Vytvoření modulu plug-in správy zdrojového](../../extensibility/internals/creating-a-source-control-plug-in.md) kódu, kde modul plug-in správy zdrojových kódů musí implementovat pevně danou sadu funkcí a zpětných volání.

  Stejně jako jakýkoli VSPackage, balíček pro správu zdrojového kódu je objekt modelu COM, který lze vytvořit pomocí `CoCreateInstance` . VSPackage zpřístupňuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní IDE implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Po vytvoření instance VSPackage získá ukazatel na lokalitu a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní, které poskytuje přístup VSPackage k dostupným službám a rozhraním v integrovaném vývojovém prostředí (IDE).

  Zápis balíčku pro správu zdrojového kódu založeného na VSPackage vyžaduje pokročilejší programovací znalosti než psaní modulu plug-in založeného na rozhraní API pro správu zdrojového kódu.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
