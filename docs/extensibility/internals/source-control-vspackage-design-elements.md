---
title: Ovládací prvky návrhu VSPackage zdroje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb741a7dc7423c27baed2cd79476239f4e41a170
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130219"
---
# <a name="source-control-vspackage-design-elements"></a>Zdrojové elementy VSPackage návrhu ovládacího prvku
Témata v této části popisují strukturu zdrojového kódu, kterou musí implementovat VSPackage pro těsná integrace. Také seznam rozhraní a služby, který zdroj ovládacího prvku VSPackage můžete implementovat a rozhraní a služeb můžete použít VSPackage zdrojového kódu z jiných [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] součásti pro podporu zdrojem řídit modelu a funkce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Struktura VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Definuje strukturu VSPackage zdrojového kódu.  
  
 [Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Uvádí související balíček rozhraní pro řízení zdrojového a služby.  
  
 [Poskytovaných služeb](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Popisuje službu Řízení zdroj poskytované VSPackage zdrojového kódu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Popisuje postup vytvoření zdrojového kódu VSPackage, který není pouze poskytuje funkce správy zdrojového ale můžete použít k přizpůsobení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zdroj ovládacího prvku uživatelského rozhraní.