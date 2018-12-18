---
title: 'Postupy: použití GetGlobalService | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: 5ce0d5657fa65cd727da2b97b3dd24735a81937a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276120"
---
# <a name="how-to-use-getglobalservice"></a>Postupy: použití GetGlobalService
V některých případech budete muset získat službu z panelu nástrojů nebo ovládací prvek kontejneru, který nebyl byl umístěn, jinak byl umístěn u poskytovatele služeb, které neví o službu, kterou chcete. Můžete například chtít zapisovat do protokolu aktivit z v rámci ovládacího prvku. Další informace o těchto a dalších scénářů najdete v tématu [postupy: řešení potíží s služby](../extensibility/how-to-troubleshoot-services.md).  
  
 Můžete získat většinu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] služby voláním statické <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> závisí na zprostředkovateli služby uložený v mezipaměti, který je inicializován poprvé jakékoli VSPackage odvozený od <xref:Microsoft.VisualStudio.Shell.Package> je umístěn. Je nutné zaručit, že tato podmínka je splněna, jinak se připravit null služby.  
  
 Naštěstí <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ve většině případů funguje správně.  
  
-   Pokud VSPackage poskytuje službu znáte jenom jiné VSPackage, VSPackage žádosti o služby je umístěn před VSPackage za předpokladu, že načtení služby.  
  
-   Pokud VSPackage vytvoří panel nástrojů, sady VSPackage je umístěn před vytvořením okna nástrojů.  
  
-   Pokud kontejneru ovládacího prvku je hostitelem nástroje okna vytvořeného rozhraním VSPackage, sady VSPackage je umístěn před vytvořením kontejneru ovládacího prvku.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Chcete-li získat službu z v rámci nástroje okna nebo ovládací prvek kontejneru  
  
-   Vložte tento kód v konstruktoru, okno nástroje nebo kontejneru ovládacího prvku:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Tento kód získá služby SVsActivityLog a přetypování na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rozhraní, které lze použít k zápisu do protokolu aktivit. Příklad najdete v tématu [postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: odstraňování potíží se službami](../extensibility/how-to-troubleshoot-services.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Základy služeb](../extensibility/internals/service-essentials.md)