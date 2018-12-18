---
title: Zdrojová architektura balíčku VSPackage ovládacího prvku | Dokumentace Microsoftu
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
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fc639214757649dcc1bee191b7b268d7b6fdbcc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802145"
---
# <a name="source-control-vspackage-architecture"></a>Architektura balíčku VSPackage správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Balíček správy zdrojového kódu je VSPackage, která používá služby, které [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje integrované vývojové prostředí. Balíček správy zdrojového kódu na oplátku poskytuje jeho funkce jako službu správy zdrojových kódů. Kromě toho balíček správy zdrojového kódu je větší variabilitu alternativní než plug-in pro integraci správy zdrojového kódu do správy zdrojových kódů [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Plug-in, který implementuje rozhraní API zdrojový ovládací prvek modulu Plug-in správy zdrojových kódů dodržuje přísné kontraktu. Například modul plug-in nejde nahradit výchozí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatelského rozhraní (UI). Kromě toho rozhraní API modulu Plug-in zdroje ovládacího prvku nepovolíte modul plug-in implementovat vlastní model správy zdrojového kódu. Balíček správy zdrojového kódu, ale překonává oba z těchto omezení. Balíček správy zdrojového kódu má plnou kontrolu nad možností ovládacího prvku zdroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatele. Kromě toho balíček správy zdrojového kódu můžete použít svůj vlastní model správy zdrojového kódu a logiku a může definovat všechny související ovládací prvek uživatelská rozhraní zdroje.  
  
## <a name="source-control-package-components"></a>Balíček součástí správy zdrojového kódu  
 Jak je znázorněno v diagramu architektury [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] součást s názvem zástupné procedury zdrojového ovládacího prvku je VSPackage, která se integruje balíček správy zdrojového kódu s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Zdrojový ovládací prvek se zakázaným inzerováním provádí následující úlohy.  
  
- Poskytuje společné uživatelské rozhraní, která je požadována pro registraci balíčku správy zdrojového kódu.  
  
- Načte balíček správy zdrojového kódu.  
  
- Nastaví balíček správy zdrojového kódu jako aktivní nebo neaktivní.  
  
  Zdrojový ovládací prvek se zakázaným inzerováním vypadat ve službě active pro balíček správy zdrojového kódu a směrovat všechny příchozí volání služby z integrovaného vývojového prostředí pro tento balíček.  
  
  Zdrojový ovládací prvek adaptér balíček je speciální zdrojového balíčku, který [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje. Tento balíček je centrální součásti pro podporu zdroj moduly plug-in správy založené na rozhraní API modulu Plug-in zdroje ovládacího prvku. Když plug-in správy zdrojových kódů je aktivní modul plug-in, odešle se zakázaným inzerováním ovládací prvek zdroje jeho události zdrojový ovládací prvek adaptér balíček. Zdrojový ovládací prvek adaptér balíček pak komunikuje se modul plug-in správy zdrojového kódu pomocí rozhraní API modulu Plug-in zdroje ovládacího prvku a také poskytuje výchozí uživatelské rozhraní, které jsou společné pro všechny zdroje moduly plug-in správy.  
  
  Když balíček správy zdrojového kódu je aktivní balíček, na druhé straně zástupné procedury zdrojového ovládacího prvku přímo komunikuje se balíček pomocí [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] rozhraní zdrojového balíčku. Balíček správy zdrojového kódu je zodpovědná za hostování vlastní zdrojového ovládacího prvku uživatelského rozhraní.  
  
  ![Obrázek architektury ovládací prvek zdroje](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
  Pro balíčky správy zdrojového kódu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] neposkytuje zdrojového kódu řízení nebo rozhraní API pro integraci. Tento rozdíl oproti naznačené v [vytváření modulu Plug-in zdrojového ovládacího prvku](../../extensibility/internals/creating-a-source-control-plug-in.md) kde má modul plug-in správy zdrojového kódu pro implementaci přísné sadu funkcí a zpětná volání.  
  
  Stejně jako jakékoli balíčku VSPackage správy zdrojového kódu balíček je objekt modelu COM, který lze vytvořit pomocí `CoCreateInstance`. Samotné sady VSPackage dává k dispozici [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Při vytvoření instance VSPackage přijímá ukazatel lokality a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní, které poskytuje přístup k balíčku VSPackage dostupné služby a rozhraní v integrovaném vývojovém prostředí.  
  
  Zápis na základě balíčku VSPackage správy zdrojového balíčku vyžaduje pokročilejší znalosti programování než zápis na rozhraní API modulu Plug-in zdroje ovládacího prvku modulu plug-in.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Začínáme](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

