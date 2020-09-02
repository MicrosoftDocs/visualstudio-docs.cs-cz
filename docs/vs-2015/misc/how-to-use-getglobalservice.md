---
title: 'Postupy: použití GetGlobalService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948179"
---
# <a name="how-to-use-getglobalservice"></a>Postupy: použití GetGlobalService
Někdy může být nutné získat službu z okna nástroje nebo kontejneru ovládacího prvku, který nebyl zadaný, nebo jinak byl vytvořen s poskytovatelem služeb, který neví o požadované službě. Například můžete chtít zapisovat do protokolu aktivit z ovládacího prvku. Další informace o těchto a dalších scénářích najdete v tématu [How to: Troubleshooting Services](../extensibility/how-to-troubleshoot-services.md).  
  
 Většinu služeb můžete získat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] voláním statické <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> spoléhá na poskytovatele služby uloženého v mezipaměti, který se inicializuje poprvé, kdy je na něm odvozená jakákoli služba VSPackage <xref:Microsoft.VisualStudio.Shell.Package> . Musíte zaručit, že je tato podmínka splněná, nebo je možné ji připravit na službu s hodnotou null.  
  
 Naštěstí <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funguje správně ve většině času.  
  
- Pokud VSPackage poskytuje službu známou pouze pro jiný VSPackage, rozhraní VSPackage požadující službu je umístěno dříve, než bude načtena služba VSPackage.  
  
- Pokud je okno nástroje vytvořeno pomocí VSPackage, rozhraní VSPackage je umístěno před vytvořením okna nástroje.  
  
- Pokud je kontejner ovládacího prvku hostován oknem nástrojů vytvořeným VSPackage, rozhraní VSPackage je umístěno před vytvořením kontejneru ovládacího prvku.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Získání služby z okna nástroje nebo kontejneru ovládacího prvku  
  
- Vložte tento kód do konstruktoru, okna nástroje nebo kontejneru ovládacího prvku:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Tento kód získá službu SVsActivityLog a přetypování ji na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rozhraní, které lze použít k zápisu do protokolu aktivit. Příklad naleznete v tématu [How to: Use a log Activity](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: řešení potíží se službami](../extensibility/how-to-troubleshoot-services.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Základy služeb](../extensibility/internals/service-essentials.md)