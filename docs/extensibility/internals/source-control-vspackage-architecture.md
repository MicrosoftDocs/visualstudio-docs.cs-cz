---
title: Správa zdrojového kódu VSPackage Architektura | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705086"
---
# <a name="source-control-vspackage-architecture"></a>Architektura balíčku VSPackage správy zdrojového kódu
Balíček správy zdrojje VSPackage, který [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá služby, které poskytuje ide. Na oplátku balíček správy zdroj poskytuje jeho funkce jako služby správy zdrojového kódu. Balíček správy zdrojového kódu je navíc všestrannější alternativou než modul plug-in správy zdrojového kódu pro integraci správy zdrojového kódu do . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

 Modul plug-in správy zdrojového kódu, který implementuje rozhraní API modulu plug-in správy zdrojového kódu, dodržuje přísnou smlouvu. Modul plug-in například nemůže [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nahradit výchozí uživatelské rozhraní (UI). Rozhraní plug-in správy zdrojového kódu navíc neumožňuje modul plug-in k implementaci vlastního modelu správy zdrojového kódu. Balíček správy zdroj, však překonává obě tato omezení. Balíček správy zdrojového kódu má úplnou [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kontrolu nad prostředí mj. Kromě toho balíček správy zdrojového kódu můžete použít vlastní model správy zdrojového kódu a logiku a můžete definovat všechna uživatelská rozhraní související s ovládacím prvkem zdrojového kódu.

## <a name="source-control-package-components"></a>Součásti balíčku pro schod zdrojového kódu
 Jak je znázorněno v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagramu architektury, součást s názvem Zdrojovládací prvek Sezakázaný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]je VSPackage, který integruje balíček správy zdrojového kódu s .

 Zdroj ovládacího prvku Se zakázaným inzerováním zpracovává následující úkoly.

- Poskytuje společné u(a) pro registraci balíčku správy zdrojového kódu.

- Načte balíček správy zdroj.

- Nastaví balíček správy zdrojového kódu jako aktivní/neaktivní.

  Ovládací prvek zdroj Sezakázaný hledá aktivní služby pro balíček správy zdrojového kódu a směruje všechna příchozí volání služby z IDE do tohoto balíčku.

  Balíček adaptéru správy zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je speciální balíček správy zdrojového kódu, který poskytuje. Tento balíček je centrální součástí pro podporu modulů plug-in správy zdrojového kódu na základě rozhraní API modulu plug-in správy zdrojového kódu. Pokud je aktivní modul plug-in správy zdrojového kódu, zástupný kód správy zdrojového kódu odešle své události do balíčku adaptéru správy zdrojového kódu. Balíček adaptéru správy zdrojového kódu zase komunikuje s modulem plug-in správy zdrojového kódu pomocí rozhraní PLUG-IN správy zdrojového kódu a také poskytuje výchozí rozhraní, které je běžné pro všechny moduly plug-in správy zdrojového kódu.

  Pokud balíček správy zdrojje je aktivní balíček, na druhé straně, ovládací prvek zdroj [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] přímo komunikuje s balíček pomocí rozhraní source-control balíček. Balíček správy zdrojového kódu je zodpovědný za hostování vlastního uj.

  ![Architektura správy zdrojového kódu – grafika](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Pro balíček správy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zdrojového kódu neposkytuje zdrojový kód správy nebo rozhraní API pro integraci. Porovnejte to s přístupem popsaným v [vytvoření modulu plug-in správy zdrojového kódu,](../../extensibility/internals/creating-a-source-control-plug-in.md) kde modul plug-in správy zdrojového kódu musí implementovat tuhou sadu funkcí a zpětná volání.

  Stejně jako všechny VSPackage, balíček správy zdrojového kódu `CoCreateInstance`je objekt COM, který lze vytvořit pomocí . VSPackage zpřístupní sám [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ide implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Po vytvoření instance VSPackage obdrží ukazatel webu a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní, které poskytuje VSPackage přístup k dostupným službám a rozhraní v ide.

  Psaní balíčku správy zdrojového kódu založeného na balíčku založeném na balíčku VSPackage vyžaduje pokročilejší znalosti programování než psaní modulu plug-in založeného na rozhraní API správy zdrojového kódu.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
