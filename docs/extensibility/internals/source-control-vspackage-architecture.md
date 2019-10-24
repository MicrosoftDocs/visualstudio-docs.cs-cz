---
title: Architektura balíčku VSPackage správy zdrojového kódu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9484aabd0080b0a44d75a8a5f6d90d9217d74b8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723354"
---
# <a name="source-control-vspackage-architecture"></a>Architektura balíčku VSPackage správy zdrojového kódu
Balíček pro správu zdrojového kódu je VSPackage, který používá služby, které poskytuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE). V případě, že balíček správy zdrojového kódu poskytuje své funkce jako službu správy zdrojového kódu. Balíček zdrojového kódu je navíc všestrannější alternativou než modul plug-in správy zdrojového kódu pro integraci správy zdrojového kódu do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Modul plug-in správy zdrojových kódů, který implementuje rozhraní API modulu plug-in správy zdrojového kódu společnost striktní smlouvou. Například modul plug-in nemůže nahradit výchozí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelské rozhraní (UI). Kromě toho rozhraní API modulu plug-in správy zdrojového kódu nepovoluje modul plug-in pro implementaci vlastního modelu správy zdrojového kódu. Balíček pro správu zdrojového kódu ale přesměruje obě tato omezení. Balíček správy zdrojového kódu má úplnou kontrolu nad prostředím pro správu zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ho uživatele. Kromě toho balíček správy zdrojového kódu může použít svůj vlastní model a logiku správy zdrojového kódu a může definovat všechna uživatelská rozhraní související se správou zdrojových kódů.

## <a name="source-control-package-components"></a>Součásti balíčku zdrojového ovládacího prvku
 Jak je znázorněno v diagramu architektury, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komponenta s názvem stub pro správu zdrojového kódu je VSPackage, který integruje balíček správy zdrojového kódu s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Zástupný kód správy zdrojového kódu zpracovává následující úkoly.

- Poskytuje společné uživatelské rozhraní, které je vyžadováno pro registraci balíčku správy zdrojového kódu.

- Načte balíček správy zdrojového kódu.

- Nastaví balíček správy zdrojového kódu jako aktivní nebo neaktivní.

  Zástupný kód správy zdrojového kódu hledá aktivní službu pro balíček zdrojového kódu a směruje všechna volání příchozích služeb z integrovaného vývojového prostředí do daného balíčku.

  Balíček adaptéru správy zdrojového kódu je speciální balíček pro správu zdrojového kódu, který [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje. Tento balíček je centrální součástí pro podporu modulů plug-in pro správu zdrojového kódu na základě rozhraní API modulu plug-in správy zdrojového kódu. Když je modul plug-in správy zdrojového kódu aktivní modulem plug-in, odešle zástupný kód správy zdrojového kódu své události do balíčku adaptéru správy zdrojového kódu. Balíček adaptéru správy zdrojového kódu pak komunikuje s modulem plug-in správy zdrojových kódů pomocí rozhraní API modulu plug-in správy zdrojového kódu a také poskytuje výchozí uživatelské rozhraní, které je běžné pro všechny moduly plug-in správy zdrojového kódu.

  Když je balíček zdrojového kódu aktivní, na druhé straně, zástupný kód správy zdrojového kódu přímo komunikuje s balíčkem pomocí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] rozhraní balíčku zdrojového ovládacího prvku. Balíček Source-Control zodpovídá za hostování vlastního uživatelského rozhraní správy zdrojového kódu.

  ![Grafika architektury správy zdrojového kódu](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Pro balíček správy zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neposkytuje pro integraci kód správy zdrojových kódů ani rozhraní API. Na rozdíl od toho s přístupem popsaným v části [Vytvoření modulu plug-in správy zdrojového](../../extensibility/internals/creating-a-source-control-plug-in.md) kódu, kde modul plug-in správy zdrojových kódů musí implementovat pevně danou sadu funkcí a zpětných volání.

  Stejně jako jakýkoli VSPackage, balíček pro správu zdrojového kódu je objekt modelu COM, který lze vytvořit pomocí `CoCreateInstance`. VSPackage zpřístupňuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Po vytvoření instance VSPackage získá ukazatel na lokalitu a rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, které poskytuje přístup VSPackage k dostupným službám a rozhraním v integrovaném vývojovém prostředí (IDE).

  Zápis balíčku pro správu zdrojového kódu založeného na VSPackage vyžaduje pokročilejší programovací znalosti než psaní modulu plug-in založeného na rozhraní API pro správu zdrojového kódu.

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-vspackages.md)